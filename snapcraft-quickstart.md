.. 32983.md

.. _snapcraft-quickstart:

# Snapcraft quickstart

This quickstart _how-to_ will guide you through the steps required to **create**, **build** and **publish** your own **snap package** with the _snapcraft_ command line tool.

The purpose of this how-to is to provide Linux developers, packagers, and users with a basic and intermediate knowledge of how to package applications as snaps. It covers the following:

- an overview of the snap ecosystem
- a detailed explanation of the Snapcraft tool and its usage
- the syntax and components of the build recipe for snaps (the _snapcraft.yaml_ file)
- the process of uploading a built snap into the Snap Store

## Here's what you need

* a basic understanding of Linux and the command line
* [Ubuntu 20.04 LTS](https://releases.ubuntu.com/20.04/), or later, installed
* 10GB of free storage space
* access to the internet

The above requirements are specific to this tutorial. Other distributions can be used, and other platforms are supported. See [Installing snapd](https://snapcraft.io/docs/installing-snapd) for details.

## Step-by-step guide

1. [Snapcraft installation and setup](snapcraft-installation-and-setup.md)
      - [Installation from the Snap Store](snapcraft-installation-and-setup.md#heading--store)
      - [Repository version or snap](snapcraft-installation-and-setup.md#heading--repository)
      - [Snapcraft LXD and Multipass backends](snapcraft-installation-and-setup.md#heading--backend)
1. [How Snapcraft builds a snap](how-snapcraft-builds-snaps.md)
   - [snapcraft.yaml](how-snapcraft-builds-snaps.md#heading--snapcraft)
      - [Main definitions inside snapcraft.yaml](how-snapcraft-builds-snaps.md#heading--definitions)
   - [Snapcraft build lifecycle](how-snapcraft-builds-snaps.md#heading--build)
   - [Snapcraft build output](how-snapcraft-builds-snaps.md#heading--output)
1. [Basic snapcraft.yaml example](basic-snapcraft-yaml-example.md)
   - [Metadata](basic-snapcraft-yaml-example.md#heading--metadata)
   - [Base](basic-snapcraft-yaml-example.md#heading--base)
   - [Confinement](basic-snapcraft-yaml-example.md#heading--confinement)
     - [Interfaces](basic-snapcraft-yaml-example.md#heading--interfaces)
   - [Build definition](basic-snapcraft-yaml-example.md#heading--build)
     - [The parts definition](basic-snapcraft-yaml-example.md#heading--parts)
     - [The apps definition](basic-snapcraft-yaml-example.md#heading--apps)
1. [Intermediate snapcraft.yaml example](intermediate-snapcraft-yaml-example.md)
   - [adopt-info](intermediate-snapcraft-yaml-example.md#heading--adopt)
   - [grade](intermediate-snapcraft-yaml-example.md#heading--grade)
   - [architectures](intermediate-snapcraft-yaml-example.md#heading--architectures)
   - [Build definition](intermediate-snapcraft-yaml-example.md#heading--build)
     - [The parts definition](intermediate-snapcraft-yaml-example.md#heading--parts)
     - [The apps definition](intermediate-snapcraft-yaml-example.md#heading--apps)
 1. [Build and publishing example](build-and-publishing-example.md)
    - [Snap build process](build-and-publishing-example.md#heading--build)
    - [Snap publication process](build-and-publishing-example.md#heading--publish)
    - [Snap Store channels](build-and-publishing-example.md#heading--channels)
    - [Next steps](build-and-publishing-example.md#heading--next)