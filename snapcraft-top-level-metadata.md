.. 8334.md

.. _snapcraft-top-level-metadata:

# Snapcraft top-level metadata

The top-level keys and values in [snapcraft.yaml](/t/the-snapcraft-format/8337) provide the snap build process, and the store, with the overarching details of a snap.

> See [Snapcraft app metadata](/t/snapcraft-app-and-service-metadata/8335) and [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336) for details on how apps and parts are configured within *snapcraft.yaml*.

Top-level details include a snap's name, version and description, alongside operational values such as its confinement level and supported architecture.

### adopt-info

Type:  `string`
(*optional*)

Incorporate external metadata via the referenced part.

See [Using external metadata](/t/using-external-metadata/4642) for more details.


### architectures

Type: `list[object]`
(*optional*)

List of build and run architectures.

For more details, see [Architectures](/t/architectures/4972).


<h3 id="heading--assumes">assumes<sup><a href=#heading--assumes>⚓</a></sup></h3>

Type: `list[string]`
(*optional*)

A list of features that must be supported by the core in order for this snap to install.  For example to make the snap only installable on certain recent version of snapd(like 2.38) you can specify:

```yaml
assumes:
- snapd2.38
```

Other potential values for _assumes_ include:
- `common-data-dir`: support for common data directory across revisions of a snap
- `snap-env`: support for the "Environment:" feature in snap.yaml
- `command-chain`: support for the "command-chain" feature for apps and hooks in snap.yaml
- `kernel-assets`: support for kernel assets in [gadget.yaml](/t/gadget-snaps/696#heading--specification), such as to include volume content in the style `$kernel:ref`

<h3 id="heading--base">base</h3>

Type: `string`
(*optional*)

A snap of type `base` to be used as the execution environment for this snap.  See [Base snaps](/t/base-snaps/11198) for further details.

Values:
| | |
|--|--|
| `bare`|  Empty base snap, useful for fully statically linked snaps and testing |
| `core` | Ubuntu Core 16 |
| `core18` | Ubuntu Core 18 |
| `core20` | Ubuntu Core 20 |
| `core22` | Ubuntu Core 22 |

<h3 id='heading--compression'>compression</h3>

Type:  `string`
(*optional*)

Sets the compression type for the snap. Can be `xz` or `lzo`. Defaults to `xz` when not specified.

Snaps are compressed using _xz_ data compression by default. This offers the optimal performance to compression ratio for the majority of snaps.

However, there are certain types of snap, such as large desktop applications, that can benefit from using LZO compression. Snaps compressed with _lzo_ are slightly larger but can decompress quicker, reducing the time it takes for freshly installed or refreshed snaps to launch.

To specify _lzo_ compression, set `compression: lzo` in your snap's _snapcraft.yaml_ and rebuild your snap, as shown in the following example:

```yaml
name: test-snapcraft-lzo
base: core18
version: "0.1"
summary: Test LZO snap
description: Test LZO snap
grade: stable
confinement: strict

# this line enables LZO compression for the snap
compression: lzo

parts:
  my-part:
    plugin: nil

apps:
  lzo-things:
    command: bin/something
```

### confinement

Type: `enum`
(*optional*)

Determines if the snap should be restricted in access or not.

Possible values are `strict` (for no access outside of declared `interfaces` through `plugs`), `devmode` (for unrestricted access) or `classic`. For more information, refer to [Confinement](/t/snap-confinement/6233).

Examples: `strict`, or `devmode`

### contact
Type: `list[string] | string`
(Introduced: Snapcraft 5.0 *optional*)

A contact for the snap in the form of a URL or email address.

### description

Type: `string`
(*mandatory*)

Multi-line description of the snap.

A more in-depth look at what your snap does and who may find it most useful.

### donation
Type: `list[string] | string`
(Introduced: Snapcraft 5.0 *optional*)

A link or list of links to receive donations for the snap.

<h3 id='heading--epoch'>epoch</h3>

type: `integer`
(*optional*)

Controls when users receive a configuration-breaking application release.

Applications and their data formats are constantly evolving, and this requires applications to periodically break data compatibility with older versions. When this happens, applications and users often need to carefully manage data migration from one version to another, and this is where epochs can help. By default, snaps have an epoch of ‘0’. When a new version breaks data compatibility with this old version, incrementing the epoch in the new release stops those old users automatically refreshing to the new version.

See [Snap epochs](/t/snap-epochs/10316) for further details.

<h3 id="heading--grade">grade</h3>

Type: `enum`
(*optional*)

Defines the quality `grade` of the snap.

Can be either `devel` (i.e. a development version of the snap, so not to be published to the `stable` or `candidate` channels) or `stable` (i.e. a stable release or release candidate, which can be released to all channels).

A snap of `type` `app` (default) cannot be set to `stable` if the `base` is not on a stable channel.

Example: `[stable` or `devel`]

<h3 id="heading--hooks">hooks</h3>

Type: `list[dict]`
(*optional*)

Hooks permit executable files to run within a snap’s confined environment when a certain action occurs.

By default, hooks run with no plugs. If a hook needs more privileges, you can use this top-level `hooks` attribute:

```yaml
hooks: # Top-level YAML attribute, parallel to `apps`
  configure: # Hook name, corresponds to executable name
    plugs: [network] # Or any other plugs required by this hook
```

See [Snapcraft hook support](/t/snapcraft-hook-support/19069) for more details.

### issues
Type: `list[string] | string`
(Introduced: Snapcraft 5.0 *optional*)

A link or list of links to report issues for the snap.

<h3 id="heading--icon">icon<sup><a href=#heading--icon>⚓</a></sup></h3>

Type: `string`
(*optional*)

Path to icon image that represents the snap in the snapcraft.io store pages and other graphical store fronts.

*Note that the [desktop menu](https://en.wikipedia.org/wiki/Start_menu) does not use this icon. It uses the icon in the  `.desktop` file of the application.*

It is a relative path to a `.png`/`.svg` file from the source tree root. The [recommended](https://forum.snapcraft.io/t/restrictions-on-screenshots-and-videos-in-snap-listings/3087/24) size is 256x256 pixels. Aspect ratio needs to be 1:1. Image size can vary from 40x40 to 512x512 px and the file size should not be larger than 256 KB.

Examples: `_package_name_.svg`, or `snap/gui/logo.png`

<h3 id="heading--layout">layout<sup><a href=#heading--layout>⚓</a></sup></h3>

Type: `list[dict]`
(*optional*)

Layouts modify the execution environment of a [strictly-confined](/t/snap-confinement/6233) snap.

With layouts, you can make elements in `$SNAP` , `$SNAP_DATA` , `$SNAP_COMMON` accessible from locations such as `/usr` , `/var` and `/etc` . This helps when using pre-compiled binaries and libraries that expect to find files and directories outside of locations referenced by `$SNAP` or `$SNAP_DATA` .

See [Snap layouts](/t/snap-layouts/7207) for more details.

Example:
```yaml
layout:
  /var/lib/foo:
    bind: $SNAP_DATA/var/lib/foo
  /usr/share/foo:
    bind: $SNAP/usr/share/foo
  /etc/foo.conf:
    bind-file: $SNAP_DATA/etc/foo.conf
```

<h3 id="heading--license">license<sup><a href=#heading--license>⚓</a></sup></h3>

Type: `string`
(*optional*)

A license for the snap in the form of an [SPDX expression](https://spdx.org/licenses/) for the license.

In the legacy Snapcraft syntax (not using the `base` key), this key is only available [through the `passthrough` key](https://forum.snapcraft.io/t/using-in-development-features-in-snapcraft-yaml/5766).

Currently, only [SPDX 2.1 expressions](https://spdx.org/spdx-specification-21-web-version) are supported.  A list of supported values are also available at  [snapd/licenses.go at master · snapcore/snapd](https://github.com/snapcore/snapd/blob/master/spdx/licenses.go).

For "or later" and "with exception" license styles refer to [the Appendix IV of the SPDX Specification 2.1](https://spdx.org/spdx-specification-21-web-version#h.jxpfx0ykyb60).

Examples: `GPL-3.0+`, `MIT`, `Proprietary`

### name
Type: `string`
(*mandatory*)

The identifying name of the snap.

It must start with an ASCII character and can only contain letters in lower case, numbers, and hyphens, and it can’t start or end with a hyphen. The name must be unique if you want to [publish to the Snap Store](/t/releasing-your-app/6795).

For help on choosing a name and registering it on the Snap Store, see [Registering your app name](/t/registering-your-app-name/6793).

Example: `my-awesome-app`


### package-repositories
Type:  `list[dict]`
(*optional*)

Adds package repositories as sources for build-packages and stage-packages, including those hosted on a PPA, the Personal Package Archive, which serves personally hosted non-standard packages.

See [Snapcraft package repositories](/t/snapcraft-package-repositories/15475) for more details.

Example:

```yaml
package-repositories:
  - type: apt
    components: [main]
    suites: [xenial]
    key-id: 78E1918602959B9C59103100F1831DDAFC42E99D
    url: http://ppa.launchpad.net/snappy-dev/snapcraft-daily/ubuntu
```

### passthrough

Type:  `type[object]`
(*optional*)

Attributes to passthrough to `snap.yaml` without validation from snapcraft.

See [Using development features in snapcraft](/t/using-in-development-features-in-snapcraft-yaml/5766) for more details.

### source-code
Type: `string`
(Introduced: Snapcraft 5.0 *optional*)

A link to the source of the snap (i.e.; the repository containing `snapcraft.yaml`).

### summary

Type: `string`
(*mandatory*)

Sentence summarising the snap.

Max len. 78 characters, describing the snap in short and simple terms.

Example: `The super cat generator`


### system-usernames

Type: `dict`
(*optional*)

Common example is `snap_daemon: shared` to use a daemon user, see [sytem-usernames](/t/system-usernames/13386) for more details.

### title

Type: `string`
(*optional*)

The canonical title of the application, displayed in the software centre graphical frontends.

Max length 40 characters.

In the legacy Snapcraft syntax (not using the `base` key), this key is only available [through the `passthrough` key](https://forum.snapcraft.io/t/using-in-development-features-in-snapcraft-yaml/5766).

Example: `My Awesome Application`


### type

Type: `enum`
(*optional*)

The type of snap, implicitly set to `app` if not set.

For more details, see: [gadget](/t/the-gadget-snap/696), [kernel](/t/the-kernel-snap/697), [base](/t/base-snaps/11198).

Example: `[app|core|gadget|kernel|base]`


### version

Type: `string`
(*mandatory*, unless using  `adopt-info`)

A user facing version to display.

This field is mandatory unless version information is provided by  `adopt-info` . See [Using external metadata](https://forum.snapcraft.io/t/using-external-metadata/4642) for details.

Max len. 32 chars. Needs to be wrapped with single-quotes when the value will be interpreted by the YAML parser as non-string.

Examples: `'1'`, `'1.2'`, `'1.2.3'`, `git` (will be replaced by a `git describe` based version string)


<h2 id="heading--plugs-and-slots-for-an-entire-snap">Plugs and slots for an entire snap</h2>

Plugs and slots for an [interface](/t/supported-interfaces/7744) are usually configured per-app or per-daemon within *snapcraft.yaml*. See [Snapcraft app metadata](/t/snapcraft-app-and-service-metadata/8335) for more details. However, `snapcraft.yaml` also enables global *plugs* and *slots* configuration for an entire snap:

### plugs

Type: `dict`
*(optional)*

These plugs apply to all `apps` and differs from **`apps.<app-name>.plugs`** in that the type is in a `dict` rather than a `list` format, `:`(colon) must be postfixed to the interface name and shouldn't start with `- `(dash-space).


### plugs.\<plug-name\>

Type: `dict`
*(optional)*

A set of attributes for a plug.

Example: `read` attribute for the `home` interface.

### plugs.\<plug-name\>.\<attribute-name\>

Type: `string`
*(optional)*

Value of the attribute.
Example: `all` for `read` attribute of the `home` interface.

### slots

Type: `dict`
*(optional)*

A set of slots that the snap provides, applied to all the `apps`.

### slots.\<slot-name\>

Type: `dict`
(*optional*)

A set of attributes of the slot.

### slots.\<slot-name\>.\<attribute-name\>

Type: `dict`
(*optional*)

Value of the attribute.

### website
Type: `string`
(Introduced: Snapcraft 5.0 *optional*)

A link to a product website from the publisher of the snap.