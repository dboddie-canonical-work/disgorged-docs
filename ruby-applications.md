.. 7824.md

.. _ruby-applications:

# Ruby applications

Linux install instructions for Ruby applications often get complicated. To prevent modules from different Ruby applications clashing with each other, developer tools like *rvm* or *rbenv* must be used.

With snaps and snapcraft, it’s one command to produce a bundle that works anywhere.

## Why are snaps good for Ruby projects?

* **Snaps install and run the same across Linux**
   They bundle the exact runtime versions required, along with all of your app's dependencies.
* **Simple creation of services**
   Create a standard app or a daemon easily.
* **Snaps are easy to discover and install**
   Millions of users can browse and install snaps graphically in the Snap Store or from the command-line.
 * **Snaps automatically update to the latest version**
   Four times a day, users' systems will check for new versions and upgrade in the background.
 * **Upgrades are not disruptive**
    Because upgrades are not in-place, users can keep your app open as it's upgraded in the background.
 * **Upgrades are safe**
    If your app fails to upgrade, users automatically roll back to the previous revision.

Ready to get started? By the end of this guide, you'll understand how to make a snap of your Ruby app that can be published in the [Snap Store](https://snapcraft.io/store), showcasing it to millions of Linux users.

> ℹ For a brief overview of the snap creation process, including how to install *snapcraft* and how it's used, see [Snapcraft overview](/t/snapcraft-overview/8940). For a more comprehensive breakdown of the steps involved, take a look at [Creating a snap](/t/creating-a-snap/6799).

## Getting started

Snaps are defined in a single YAML file placed in the root folder of your project. The following example shows the entire *snapcraft.yaml* file for an existing project, [Markdown lint tool](https://github.com/snapcraft-docs/mdl). Don't worry, we’ll break this down.


## Travis

Snaps are defined in a single yaml file placed in the root of your project. The Travis example shows the entire `snapcraft.yaml` for an existing project, leveraging the existing `gemspec` to satisfy runtime requirements. We'll break this down.

```yaml
name: test-mdl
version: "0.5.0"
summary: Markdown lint tool
description: |
  Style checker/lint tool for markdown files

confinement: devmode
base: core18

parts:
  test-mdl:
    source: .
    plugin: ruby
    gems:
      - rake
      - bundler
    override-build: |
      snapcraftctl build
      rake install
    build-packages:
      - git
apps:
  test-mdl:
    command: bin/mdl
```

### Metadata

The `snapcraft.yaml` file starts with a small amount of human-readable metadata, which usually can be lifted from the GitHub description or project README.md. This data is used in the presentation of your app in the Snap Store.

```yaml
name: test-mdl
version: "0.5.0"
summary: Markdown lint tool
description: |
  Style checker/lint tool for markdown files
```

The `name` must be unique in the Snap Store. Valid snap names consist of lower-case alphanumeric characters and hyphens. They cannot be all numbers and they also cannot start or end with a hyphen.

Version is an arbitrary string or number.

The `summary` can not exceed 79 characters. You can use a chevron '>' in the `description` key to declare a multi-line description.

#### Base

The base keyword declares which _base snap_ to use with  your project.  A base snap is a special kind of snap that provides a run-time environment alongside a minimal set of libraries that are common to most applications:

```yaml
base: core18
```
As used above, [`core18`](https://snapcraft.io/core18) is the current standard base for snap building and is based on [Ubuntu 18.04 LTS](http://releases.ubuntu.com/18.04/).

See [Base snaps](/t/base-snaps/11198) for more details.

#### Security model

The next section describes the level of confinement applied to your app.

```yaml
confinement: devmode
```
Snaps are containerised to ensure more predictable application behaviour and greater security. Unlike other container systems, the shape of this confinement can be changed through a set of interfaces. These are declarations that tell the system to give permission for a specific task, such as accessing a webcam or binding to a network port.

It's best to start a snap with the confinement in warning mode, rather than strictly applied. This is indicated through the `devmode` keyword. When a snap is in devmode, runtime confinement violations will be allowed but reported. These can be reviewed by running `journalctl -xe`.

Because devmode is only intended for development, snaps must be set to strict confinement before they can be published as "stable" in the Snap Store. Once an app is working well in devmode, you can review confinement violations, add appropriate interfaces, and switch to strict confinement.

### Parts

Parts define what sources are needed to assemble your app. Parts can be anything: programs, libraries, or other needed assets, but for now, we're only going to use one part: the *mdl* source code.

```yaml
parts:
  test-mdl:
    source: .
    plugin: ruby
    gems:
      - rake
      - bundler
    override-build: |
      snapcraftctl build
      rake install
    build-packages:
      - git
```

For more details on Ruby-specific metadata, see [The Ruby plugin](/t/the-ruby-plugin/8587).

### Apps

Apps are the commands you want to expose to users and any background services your application provides. Each key under `apps` is the command name that should be made available on users' systems.

The `command` specifies the full path to the binary to be run. This is resolved relative to the root of your snap contents.

```yaml
apps:
  test-mdl:
    command: bin/mdl

```

If your application is intended to run as a service you simply add the line `daemon: simple` after the command keyword. This will automatically keep the service running on install, update and reboot.

If your command name matches the snap  `name`, users will be able run the command directly. If the names differ, then apps are prefixed with the snap  `name`  (`offlineimap.command-name`, for example). This is to avoid conflicting with apps defined by other installed snaps.

You can request an alias on the  [Snapcraft forum](https://forum.snapcraft.io/t/process-for-reviewing-aliases-auto-connections-and-track-requests/455) if your command name and snap name do not match but you don’t want your command prefixed. These aliases are set up automatically when your snap is installed from the Snap Store.

### Building the snap

You can download the example repository with the following command:

```bash
$ git clone https://github.com/snapcraft-docs/mdl
```

After you've created the *snapcraft.yaml*, you can build the snap by simply executing the *snapcraft* command in the project directory:

```bash
$ snapcraft
Using 'snapcraft.yaml': Project assets will be searched for from the 'snap' directory.
Launching a VM.
[...]
Snapped test-mdl_0.5.0_amd64.snap
```
The resulting snap can be installed locally. This requires the `--dangerous` flag because the snap is not signed by the Snap Store. The `--devmode` flag acknowledges that you are installing an unconfined application:

```bash
$ sudo snap install test-mdl_*.snap --devmode --dangerous
```

You can then try it out:

```bash
$ test-mdl -h
```

Removing the snap is simple too:

```bash
$ sudo snap remove test-mdl
```
You can also clean up the build environment, although this will slow down the next initial build:

```bash
$ snapcraft clean
```

By default, when you make a change to snapcraft.yaml, snapcraft only builds the parts that have changed. Cleaning a build, however, forces your snap to be rebuilt in a clean environment and will take longer.

## Publishing your snap

To share your snaps you need to publish them in the Snap Store. First, create an account on [the dashboard](https://dashboard.snapcraft.io/dev/account/). Here you can customise how your snaps are presented, review your uploads and control publishing.

You’ll need to choose a unique “developer namespace” as part of the account creation process. This name will be visible by users and associated with your published snaps.

Make sure the `snapcraft` command is authenticated using the email address attached to your Snap Store account:

```bash
$ snapcraft login
```

### Reserve a name for your snap

You can publish your own version of a snap, provided you do so under a name you have rights to. You can register a name on [dashboard.snapcraft.io](https://dashboard.snapcraft.io/register-snap/), or by running the following command:

```bash
$ snapcraft register mypythonsnap
```

Be sure to update the `name:` in your `snapcraft.yaml` to match this registered name, then run `snapcraft` again.

### Upload your snap

Use snapcraft to push the snap to the Snap Store.

```bash
$ snapcraft upload --release=edge mynodesnap_*.snap
```

If you’re happy with the result, you can commit the snapcraft.yaml to your GitHub repo and [turn on automatic builds](https://build.snapcraft.io) so any further commits automatically get released to edge, without requiring you to manually build locally.

Congratulations! You've just built and published your first Go snap. For a more in-depth overview of the snap building process, see [Creating a snap](/t/creating-a-snap/6799).