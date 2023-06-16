.. 23801.md

.. _validation-sets:

# Validation sets

A validation set is an [assertion](/t/assertions/6155) that lists specific snaps that are either required to be installed together or are permitted to be installed together on a device or system.

One or more validation sets can be used to ensure only specific snaps are installed, and optionally, only specific snaps at fixed [revisions](/t/glossary/14612#heading--revision). They can help a set of interdependent snaps maintain their testing and certification integrity, as well as help orchestrate their updates. But they can equally be used to simplify dependency deployment and to help manage devices.

## Prerequisites

Validation set functionality is currently under active development and there are several considerations that need to be made before using it:
- A developer account is also required, along with your developer id.</br>
  (_see [Create a developer account](/t/create-a-developer-account/6760#heading--developer-id) for further details_)
- Snapd version 2.50 and [Snapcraft](/t/snapcraft-overview/8940) version [4.7](/t/release-notes-snapcraft-4-7/24252), or newer, are required.
- **Currently, in order to enforce a validation set, the following is also required:**
  - a [brand store](/t/glossary/14612#heading--brand-store) account
  - the validation set's `name`, `account-id` and listed snaps, need to be added to an allowlist in the store backends (this is done by filing a brand store support ticket).
  - Snapd version 2.54

See below for further details on the following:
- [Creating a validation set](#heading--creating)
- [Listing a validation set](#heading--listing)
- [Monitoring assertion validity](#heading--using)
- [Enforcing assertion validity](#heading--enforcing)

---

<h2 id='heading--creating'>Creating a validation set</h2>

To create a validation set, use the `snapcraft edit-validation-sets` command:

```bash
snapcraft edit-validation-sets <account-id> <set-name> <sequence>
```

This command requires your developer account id, an arbitrary name for the validation set, and a sequence number. The sequence number starts at 1 and is incremented at the developer's discretion when there's a substantial change or update to the validation set:

```bash
snapcraft edit-validation-sets xSfWKGdLoQBoQx88vIM1MpbFNMq53t1f myset1 1
```

An additional `--key-name` argument can be used to specify a key other than the default.

A text editor will open containing a template for a validation set assertion that needs to be filled in by the developer issuing the assertion.

[details=validation-set template]
```yaml
account-id: <account-id>
name: <set-name>
sequence: <sequence>
# The revision for this validation set
# revision: 0
snaps:
#  - name: <name>  # The name of the snap.
#    id:   <id>    # The ID of the snap. Optional, defaults to the current ID for
                   # the provided name.
#    presence: [required|optional|invalid]  # Optional, defaults to required.
#    revision: <n> # The revision of the snap. Optional.
```
[/details]

The template validation set assertion needs to be populated with the details of the snaps you wish to include in the set. These are listed beneath the `snaps:` section, and each snap can use the following fields:

- **`name`** (*required*):
   The name of the snap, as you find on the store or in _snap search_.
- **`id`** (*optional*):
   The unique snap-id of the snap (see _snap info \<snap name\>_ ).
   Defaults to the snap-id of the named snap.
- **`presence`** (*optional*):
   Can be either `required`, `optional` or `invalid`.
   `required` snaps need to be installed, `optional` snaps are permitted to be installed and `invalid` snaps explicitly must not be installed.
   Defaults to _required_.
- **`revision`** (*optional*):
   Specifies which [revision](/t/glossary/14612#heading--revision) of the snap needs to be installed.

The following is a populated example of a validation set assertion:

```yaml
account-id: xSfWKGdLoQBoQx88vIM1MpbFNMq53t1f
name: myset1
# revision: 0
sequence: 1
snaps:
  - name: hello-world
    id: buPKUD3TKqCOgLEjjHx5kSiCpIs5cMuQ
    presence: required
  - name: test-snapd-base-bare
    id: oXC9AkhtCxhlY80KZA3peZzWbnO4xPOT
    presence: optional
  - name: bare
    id: EISPgh06mRh1vordZY9OZ34QHdd7OrdR
    presence: optional
```

We recommend making a copy of the saved validation set assertion before closing the editor.  Closing the editor will first check the integrity of the assertion before automatically uploading it to the store.

To modify the assertion at a later point, run the same `snapcraft edit-validation-sets` command with the same name but an incremented sequence number and/or revision.

<h2 id='heading--listing'>Listing validation sets</h2>

Use the `snapcraft list-validation-sets` command to check which validation sets area available in the store:

```bash
$ snapcraft list-validation-sets
Account-ID                       Name      Sequence  Revision  When
xSfWKGdLoQBoQx88vIM1MpbFNMq53t1f myset1    1         0         2021-04-08
xSfWKGdLoQBoQx88vIM1MpbFNMq53t1f testset1  2         0         2021-03-31
```

To list only validation-sets with a specific set name, use the additional `--name` argument:

```bash
$ snapcraft list-validation-sets --name myset1
Account-ID                       Name      Sequence  Revision  When
xSfWKGdLoQBoQx88vIM1MpbFNMq53t1f myset1    1         0         2021-04-08
```

An additional `--sequence` argument can be used to list validation sets with a specific sequence number:

```bash
$ snapcraft list-validation-sets --name myset1 --sequence 1
Account-ID                       Name      Sequence  Revision  When
xSfWKGdLoQBoQx88vIM1MpbFNMq53t1f myset1    1         0         2021-04-08
```

By default, only the most _latest_ validation sets are listed. To list every validation set available, add the `--all` argument.

<h2 id='heading--using'>Monitoring assertion validity</h2>

The `snap validate --monitor` command is used to enable monitoring of a validation assertion on the system; in this mode the constraints of the assertion are not enforced (e.g. snaps may get automatically refreshed to newer revisions that make the assertion invalid as show in the next example):

```bash
snap validate --monitor xSfWKGdLoQBoQx88vIM1MpbFNMq53t1f/testset1
```

The `snap validate` command, with no further arguments, checks whether the `snaps:` rules for all validation set assertions on the store are valid for the system:

```bash
$ snap validate
Validation                                 Mode     Seq  Current    Notes
xSfWKGdLoQBoQx88vIM1MpbFNMq53t1f/myset1    monitor  1    valid
xSfWKGdLoQBoQx88vIM1MpbFNMq53t1f/testset1  monitor  2    invalid
```

An assertion is invalid if snaps in the system do not satisfy the constraints of the assertion, such as if required snaps are missing or whether unwanted snaps are present. Multiple validation sets can be used, as shown above, as long as they don't have conflicting constraints and that they can cover different sets of snaps.

A specific validation set can be checked with `snap validate <account id>/<validation set name>`, with an optional sequence point set by adding `=<sequence>` to the validation set name:

```bash
$ snap validate xSfWKGdLoQBoQx88vIM1MpbFNMq53t1f/myset1=1
valid
```

A validation set assertion can be _pinned_ by the system administrator at the given sequence number,:

```bash
snap validate --monitor xSfWKGdLoQBoQx88vIM1MpbFNMq53t1f/testset1=3
```

A pinned validation set is kept at the given sequence number, even if there's a higher sequence number in the store. However, the validation will be updated to a newer version if one becomes available with the same sequence number.

Monitor mode validation requires a manual action (`snap validate`, as shown above), but nothing is enforced in the system. Only when _enforce mode_ has been implemented will validation sets have an impact on the system and will prevent installing/removing snaps that violate an assertion's constraints.

Finally, to remove a validation set from the system, use the `--forget` argument:

```bash
snap validate --forget xSfWKGdLoQBoQx88vIM1MpbFNMq53t1f/myset1
```

<h2 id='heading--enforcing'>Enforcing assertion validity</h2>

When enforcing a validation set, snapd will ensure that:

* Snaps required by a validation set are both present and, if specified, at the correct revision. Attempting to remove a required snap will result in an error and the process will be rejected.
*  Snaps are only refreshed to newer revisions if they continue to satisfy whatever validation sets are in use.
* Invalid snaps are not allowed to be installed. Attempting to install them will result in an error.

A validation set can be enforced by adding the `--enforce` argument to the ‘snap validate’ command:

```bash
snap validate --enforce xSfWKGdLoQBoQx88vIM1MpbFNMq53t1f/myset1
```

Every snap required by a validation set needs to be  installed before enforcing is enabled. The snap daemon will neither install missing snaps nor remove invalid snaps. If there are snaps missing, or invalid snaps installed, the assertion will simply become invalid.

After enforcement is enabled, snapd ensures the consistency of the enforced validation sets, and the snaps they reference, during install, refresh and remove operations.

During auto-refreshes, or manual refreshes, enforced validation set assertions on the system may be refreshed to newer revisions if the assertion is:
- present in the store
- not pinned to a specific sequence

An assertion will move to the latest sequence if present in the store and if the installed snaps, including any newer revisions in the store, still satisfy their respective validation set assertions.

In this way, the `snapcraft edit-validation-sets` command can be used to control the updates of multiple snaps at the same time.

For brief periods during multi-snap updates, different snap revisions, from previous and incoming validation set sequence points, can co-exist. validation-sets enforcement is not intended to deal with any breaking hard version dependencies during transitions.

As with monitor mode, enforcing can be disabled for select validation sets with the ‘snap validate --forget’ command.

When using `snap install` and `snap refresh`, the `--ignore-validation` flag can be added to bypass validation set enforcement for the snaps affected. Doing so will ignore the validation of the given snap, and for subsequent refresh operations. This may result in the validation set becoming _invalid_ in `snap validate` output.