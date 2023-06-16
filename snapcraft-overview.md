.. 8940.md

.. _snapcraft-overview:

# Snapcraft overview

[Snapcraft](https://snapcraft.io/snapcraft) is a powerful and easy to use command line tool for building [snaps](/t/getting-started/3876). It helps you to:
- build and then publish your snaps on the [Snap store](https://snapcraft.io/store)
- use [channels, tracks and branches](/t/channels/551) to finely control updates and releases
- build and debug snaps within a confined environment
- update and iterate over new builds without rebuilding the environment
- test and share your snaps locally

On Linux distributions [with snap support](/t/installing-snapd/6735), the easiest way to install *snapcraft* is via its snap:

```bash
sudo snap install snapcraft --classic
```
The `--classic` argument is required because snapcraft uses [classic confinement](/t/snap-confinement/6233).

Snapcraft can also be installed and run on Apple's macOS. See [Install snapcraft on macOS](/t/installing-snapcraft/20334#heading--macos) for details.

See below for a general overview of Snapcraft's capabilities, and see [Creating a snap](/t/creating-a-snap/6799) for a more detailed look at the process, alongside a selection of self-contained examples for some popular languages and frameworks, including [Go](/t/go-applications/7818), [Python](/t/python-apps/6741) and [C/C++](/t/c-c-applications/7817).

> ⓘ If you're using an **apt** installed version of snapcraft, such as the package for [Ubuntu 18.04 LTS](http://releases.ubuntu.com/18.04/), you need to remove this (`sudo apt remove snapcraft`) and install snapcraft from its snap to access the latest features.

## Working with snapcraft

At the heart of the snapcraft build process is a file called [snapcraft.yaml](/t/the-snapcraft-format/8337). This file describes a snap's build dependencies and run-time requirements, it integrates remote repositories and extensions, and runs custom scripts and hooks for better integration with CI systems.

[Snapcraft 3.0](/t/snapcraft-release-notes/10721), and later releases, are designed to use *bases* (see [Base snaps](/t/base-snaps/11198)) and [LXD](https://linuxcontainers.org/lxd/introduction/) or [Multipass](https://multipass.run/) to both simplify the build process and to confine the build environment within a virtual machine. Confining the build in this way isolates potentially conflicting libraries and other files from your host system, and vice-versa.

Snapcraft offers a variety of options when using LXD and Multipass. See [Build options](/t/build-options/14250) for details on build options and [build providers](t/build-on-lxd/4157) for details on interacting with LXD and Multipass.

<h3 id='heading--creating-snapcraft'>Creating snapcraft.yaml</h3>

To get started, run `snapcraft init`. This creates a buildable snapcraft.yaml template within a snap sub-directory relative to your current filesystem location. If the command cannot be found, make sure `/snap/bin` is on your PATH.

The typical snap build process centres on iterating over the configuration of  *parts*, *plugins* and *interfaces* within this snapcraft.yaml file:

- **parts** are the raw building blocks of a snap, used to collect and build binaries and their dependencies.
- **[plugins](/t/snapcraft-plugins/4284)** are used within parts to better integrate projects using languages and framework.
- **[interfaces](/t/interface-management/6154)** enable resources from one snap to be shared with another, and with the host system.

The following lists how you might want to approach building a new snap for your application with [snapcraft.yaml](/t/the-snapcraft-format/8337):
 1. describe your application with [top-level metadata](/t/snapcraft-top-level-metadata/8334)
 1. use [parts metadata](/t/snapcraft-parts-metadata/8336) to import and build your application and its dependencies
    -  incorporate *plugins* within parts to easily integrate applications using specific languages and frameworks, or work with binary files directly. You can also [write your own](/t/writing-local-plugins/5125) plugin.
    - use [plugin metadata](/t/supported-plugins/8080) to locate your project, or sync with a remote repository
    - set build dependencies, if required, and any run-time dependencies
 1. add [interface metadata](/t/snapcraft-app-and-service-metadata/8335) to connect external system resources to your application

<h2 id='heading--building-your-snap'>Building your snap</h2>

When you are ready to test the contents of snapcraft.yaml, simply run `snapcraft --debug` in the same directory where you initialised the snap.

If this is the first time you've built a snap with snapcraft, you will either need to have a build provider installed, or you will be prompted to install it before the build continues:

```bash
$ snapcraft --debug
LXD is required but not installed. Do you wish to install LXD and configure it with the defaults? [y/N]: y
```

The `--debug` argument isn't necessary, but it helps when testing a new snapcraft.yaml.

With `--debug`, if snapcraft encounters an error it will automatically open a shell *within* your snap's build environment. You can then explore the build issue directly, working on your project within the *parts* directory, or the files being staged within *prime*, depending on the build stage when the error occurred.

> ⓘ  See [iterating over a build](/t/iterating-over-a-build/12143) for more information about the `--debug` flag (and the related flags `--shell` and `--shell-after`).

Critically, you can update snapcraft.yaml *outside* of the build environment and run `snapcraft` *within* the build environment to incorporate any external changes and continue with the build. If there are no further errors, your snap will be built.

> ⓘ  See [Debugging building snaps](/t/debugging-building-snaps/6274) for common problems and their solutions.

To see snapcraft build the template created by *snapcraft init*, simply run `snapcraft --debug`:

```bash
$ snapcraft --debug
Launching instance...
Executed: pull my-part
Executed: overlay my-part
Executed: build my-part
Executed: stage my-part
Executed: prime my-part
Executed parts lifecycle
Generated snap metadata
Created snap package my-snap-name_0.1_amd64.snap
```

The build process will proceed through the [Snapcraft lifecycle](/t/parts-lifecycle/12231), installing and building your project's dependencies, as described by your snapcraft.yaml. The time this takes will depend on the complexity of your project and the capabilities of your system.

<h2 id='heading--testing'>Testing your snap locally</h2>

After a snap has been built, it can be installed locally with the `--devmode` flag, enabling your unsigned and unconfined snap to be installed:

```bash
sudo snap install my-snap-name_0.1_amd64.snap --devmode
my-snap-name 0.1 installed
```
For a more comprehensive and iterative break-down of the snap building process, see [Creating a snap](/t/creating-a-snap/6799).

[note type="important"]
ⓘ To see what's new in each release of Snapcraft, take a look at [Snapcraft release notes](/t/snapcraft-release-notes/10721).
[/note]