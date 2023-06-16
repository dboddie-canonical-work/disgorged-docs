.. 18768.md

.. _flutter-applications:

# Flutter applications

[Flutter](https://flutter.dev/) is Google's open source tookit to help create beautiful, responsive, and natively compiled applications for mobile, web and desktop.

## Why are snaps good for Flutter projects?

* **Snaps are easy to discover and install**</br>
  Millions of users browse and install snaps from the [Snap Store](https://snapcraft.io/store) and the command line.
* **Snaps install and run the same across Linux**</br>
  Your snap works across many distributions with the exact versions of any dependencies.
* **Snaps automatically update to the latest version**</br>
  Four times a day, users’ systems will check for new versions and upgrade in the background.
* **Upgrades are not disruptive**</br>
  Upgrades are not in-place and apps can be open while they upgrade in the background.
* **Upgrades are safe**</br>
  If your app fails to upgrade, users automatically roll back to the previous revision.

## Build a snap in 20 minutes

Ready to get started? By the end of this guide, you'll understand how to make a snap of your Flutter app that can be published in the [Snap Store](https://snapcraft.io/store), showcasing it to millions of Linux users.

> ℹ For a brief overview of the snap creation process, including how to install *snapcraft* and how it's used, see [Snapcraft overview](snapcraft-overview.md). For a more comprehensive breakdown of the steps involved, take a look at [Creating a snap](creating-a-snap.md).

## Getting started

Snaps are defined in a single YAML file placed in the root folder of your project. We're going to an example template project, but we'll show a more complex example later.

The following shows the entire *snapcraft.yaml* file [super-cool-app](https://github.com/snapcraft-docs/super-cool-app), our simple template project:

```yaml
name: super-cool-app
version: git
summary: Super Cool App
description: Super Cool App that does everything!
confinement: strict
base: core18
grade: stable
architectures:
  - build-on: [ amd64 ]
  - build-on: [ arm64 ]

apps:
  super-cool-app:
    command: super_cool_app
    extensions: [flutter-stable]

parts:
  super-cool-app:
    source: .
    plugin: flutter
    flutter-target: lib/main.dart # The main entry-point file of the application
```

Don't worry, we’ll break this down.

#### Metadata

The `snapcraft.yaml` file starts with a small amount of human-readable metadata, which usually can be lifted from the GitHub description or project README.md. This data is used in the presentation of your app in the Snap Store.

```yaml
name: super-cool-app
version: '1.0'
summary: Super Cool App
description: Super Cool App that does everything!
```

The `name` must be unique in the Snap Store. Valid snap names consist of lower-case alphanumeric characters and hyphens. They cannot be all numbers and they also cannot start or end with a hyphen.

The `version` string can be an arbitrary version, such as `1.0` in our example, or keywords such as `git`, to import a version string from a git tag or commit, for instance. Versions carry no semantic meaning in snaps.

The `summary` can not exceed 79 characters. You can use a chevron '>' in the `description` key to declare a multi-line description.

#### Security model

The next section describes the level of confinement applied to your app.

```yaml
confinement: strict
```
Snaps are containerised to ensure more predictable application behaviour and greater security. Unlike other container systems, the shape of this confinement can be changed through a set of interfaces. These are declarations that tell the system to give permission for a specific task, such as accessing a webcam or binding to a network port.

It's best to start a snap with the confinement in warning mode, rather than strictly applied. This is indicated through the `devmode` keyword. When a snap is in devmode, runtime confinement violations will be allowed but reported. These can be reviewed by running `journalctl -xe`.

Because devmode is only intended for development, snaps must be set to `strict` confinement before they can be published as "stable" in the Snap Store. Once an app is working well in devmode, you can review confinement violations, add appropriate interfaces, and switch to strict confinement (our example uses _strict_ because we know it's working as expected).

#### Base

The base keyword declares which _base snap_ to use with  your project.  A base snap is a special kind of snap that provides a run-time environment alongside a minimal set of libraries that are common to most applications:

```yaml
base: core18
```
As used above, [`core18`](https://snapcraft.io/core18) is the current standard base for snap building and is based on [Ubuntu 18.04 LTS](http://releases.ubuntu.com/18.04/).

See [Base snaps](base-snaps.md) for more details.

#### Parts

Parts define what sources are needed to assemble your app. Parts can be anything: programs, libraries, or other needed assets.

```yaml
parts:
  super-cool-app:
    plugin: flutter
    source: https://github.com/snapcraft-docs/super-cool-app
    flutter-target: lib/main.dart
```

In this case, we have one: the *super-cool-app* source code, which is going to be built using the [flutter](the-flutter-plugin.md) plugin. Parts can retrieve data from local directories, remote git repositories, or tarballs, and the Flutter plugin performs all the tasks necessary to build the code.

See [Environment variables](environment-variables.md) for details on locations you can use from within _snapcraft.yaml_.

#### Apps

Apps are the commands and services exposed to end users. We use this section to link the binary built in the previous step, confusingly called `build`, to be the _super_cool_app_ command:

```yaml
apps:
  super-cool-app:
    command: super_cool_app
    extensions: [flutter-stable]
```

If your command name matches the snap `name`, users will be able run the command directly.

If the names differ, then apps are prefixed with the snap `name` (`flutter-gallery.command-name`, for example). This is to avoid conflicting with apps defined by other installed snaps.

If you don’t want your command prefixed you can request an alias for it on the [Snapcraft forum](https://snapcraft.io/docs/process-for-aliases-auto-connections-and-tracks). These are set up automatically when your snap is installed from the Snap Store.

The `extensions` keyword is used to easily incorporate Flutter's common set of requirements. See [Snapcraft extensions](snapcraft-extensions.md) for further details.

If your application is intended to run as a service you simply add the line `daemon: simple` after the command keyword. This will automatically keep the service running on install, update, and reboot.

### Building the snap

First, make sure you've installed [Snapcraft](snapcraft-overview.md) and create a new directory for your Flutter project.

Inside that directory, type `snapcraft init`. This creates an additional subdirectory, called `snap`, and inside that creates a template _snapcraft.yaml_ file.

Edit the created _snapcraft.yaml_ to contain the Flutter example shown earlier.

After you've created the *snapcraft.yaml*, you can build the snap by simply executing the *snapcraft* command in the project directory:

```bash
$ snapcraft
Using 'snapcraft.yaml': Project assets will be searched for from the 'snap' directory.
Launching a VM.
Launched: snapcraft-super-cool-app
[...]
Pulling flutter-extension
[...]
Building super-cool-app
[...]
Staging flutter-extension
Staging gnome-3-28-extension
Staging super-cool-app
Priming flutter-extension
Priming gnome-3-28-extension
Priming super-cool-app
'grade' property not specified: defaulting to 'stable'.
Snapping |
Snapped super-cool-app_1.0_amd64.snap
```

The build process may take some time as both Flutter and the Dart SDK from Flutter are downloaded and installed into the build environment, but they won't be downloaded again with subsequent builds unless the environment is reset.

The resulting snap can be installed locally. This requires the `--dangerous` flag because the snap is not signed by the Snap Store, or if you're testing pre-confinement, the `--devmode` flag acknowledges that you are installing an unconfined application:

```bash
sudo snap install super-cool-app_1.0_amd64.snap --dangerous
```

You can then try it out:

```bash
super-cool-app
```

![Running example Flutter application](https://assets.ubuntu.com/v1/f12e5af3-flutter_01.png)

Removing the snap is simple too:

```
sudo snap remove super-cool-app
```

You now have a snap you can deploy and upload to the [Snap Store](https://snapcraft.io/store). See [Releasing your app](releasing-your-app.md) for more details, and to get a deeper insight into the snap building process, start with the [Snapcraft checklist](snapcraft-checklist.md).