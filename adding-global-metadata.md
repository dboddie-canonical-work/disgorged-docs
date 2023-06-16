.. 11486.md

.. _adding-global-metadata:

# Adding global metadata

Global metadata attributes are used within [snapcraft.yaml](/t/the-snapcraft-format/8337) to identify the snap locally, and after publishing to the [Snap Store](https://snapcraft.io/store), to identify your snap to  users and potential users.

Attributes include a snap's name and description, its level of confinement, and where the application icon can be found.

```yaml
name: qfsview
summary: Visualise storage utilisation.
description: |
    qFSView displays files and folders as a rectangle with an
    area proportional to the storage they and their children use.
version: 1.0
icon: gui/qfsview.png
base: core18
grade: stable
confinement: strict
```
For the complete list of global metadata, see [Snapcraft top-level metadata](/t/snapcraft-top-level-metadata/8334).

## Recommended global metadata

Global metadata is a mixture of mandatory and optional values.

You can generate a buildable template of both required and recommended values with the `snapcraft init` command in a new project folder (see [Snapcraft overview](/t/snapcraft-overview/8940) for more details).

The following attributes are mandatory:

- **`name`**
A snap's name is important. It must start with an ASCII character and can only contain 1) letters in lower case, 2) numbers, and 3) hyphens, and it can't start or end with a hyphen. For the  [Snap Store](https://snapcraft.io/store), it also needs to be both unique and easy to find.

  For help on choosing a name and registering it on the Snap Store, see [Registering your app name](/t/registering-your-app-name/6793).

- **`summary`**
The *summary* is a short descriptive sentence to tell prospective users about an application's
primary purpose, in fewer than 80 characters.

- **`description`**
Unlike the *summary*, the description can be as verbose as you need it to be.  The above snippet shows the description text following a pipe symbol (`|`), which is used in YAML to maintain newline formatting in multiline text blocks.

  The following, for example, will ensure both _Line one_ and _Line two_ appear on separate lines:

   ```yaml
   description: |
       Line one
       Line two
   ```

   While you shouldn't write thousands of words, the more details you provide, the more likely people are to discover and use your application. Feature lists, update descriptions, a brief *Getting started* guide, are legitimate uses for the *description*.

- **`version`**
While having a value for *version* is mandatory, its value can be anything. Setting this to something like `test` makes sense while you're first building your snap, and you can later replace this with a specific version, or a reference to a script that replaces the version number automatically.

  The value for *version* is also commonly imported for external metadata. See [Using using external metadata](/t/using-external-metadata/4642) for further details.

The following attributes should also be included:

- **`base`**
A base snap is a special kind of snap that provides a run-time environment with a minimal set of libraries that are common to most applications.

  See [Base snaps](/t/base-snaps/11198) for help selecting a base for your snap.

- **`grade`**
This should initially be `devel` and changed to `stable` when you have a snap ready for release.

- **`confinement`**
A snap’s confinement level is the degree of isolation it has from your system. When first building a  snap, set this to `devmode` to initially limit the side-effects of confinement until you have a working snap.

  See [Snap confinement](/t/snap-confinement/6233) for further details.

For convenience, and to help avoid duplicating sources,  external metadata such as [AppStream](https://snapcraft.io/docs/using-external-metadata#heading--appstream) can be imported into *snapcraft.yaml*. See [Using external metadata](/t/using-external-metadata/4642) for further details.

Two further global attribites are `apps:` and `parts:`. These  expand into separate sections that deal with how your snap is built and where its various resources are located.  See [Adding parts](/t/adding-parts/11473) for the next logical step in snap building.