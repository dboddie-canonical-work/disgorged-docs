.. 20334.md

.. _installing-snapcraft:

# Installing snapcraft

[Snapcraft](https://snapcraft.io/snapcraft) is a powerful and easy to use command line tool for building [snaps](https://snapcraft.io/docs/quickstart-guide). It helps you to both build and publish snaps, test and share them locally, and keep them all updated.

For a general overview of what Snapcraft is capable of, and how to build your first snap, take a look at our [Quickstart guide](snapcraft-overview.md), and see below for installation instructions:

- [Linux distributions](#heading--linux)
- [macOS](#heading--macos)

<h2 id='heading--linux'>Install snapcraft on Linux</h2>

On Linux distributions [with snap support](https://snapcraft.io/docs/installing-snapd), the easiest way to install *snapcraft* is via its snap:

```bash
$ sudo snap install snapcraft --classic
```
The `--classic` argument is required because snapcraft uses [classic confinement](snap-confinement.md).


> ⓘ If you're using an **apt** installed version of snapcraft, such as the package for [Ubuntu 18.04 LTS](http://releases.ubuntu.com/18.04/), you need to remove this (`sudo apt remove snapcraft`) and install snapcraft from its snap to access the latest features.

<h2 id='heading--macos'>Install snapcraft on macOS</h2>

Snapcraft can also be installed and run on Apple's macOS. See [Install snapcraft on macOS](https://snapcraft.io/docs/install-snapcraft-on-macos) for details.

On Apple macOS Yosemite (or later), Snapcraft can be installed via [Homebrew](https://formulae.brew.sh/formula/snapcraft) and used to build snaps within the macOS environment.

Prerequisites:
- Make sure you have the [Homebrew package manager](https://brew.sh/#install) installed
- Download and run the [Multipass installer](https://discourse.ubuntu.com/t/installing-multipass-on-macos/8329) to install Multipass

To install *snapcraft*, open 'Terminal` and enter the following:

```bash
$ brew install snapcraft
```

When the process completes, the *snapcraft* command will be installed and ready to go. See [Snapcraft overview](snapcraft-overview.md) for help getting started.