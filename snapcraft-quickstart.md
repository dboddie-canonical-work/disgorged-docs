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

The above requirements are specific to this tutorial. Other distributions can be used, and other platforms are supported. See [Installing snapd](/t/installing-snapd/6735) for details.

## Step-by-step guide

1. [Snapcraft installation and setup](/t/snapcraft-installation-and-setup/32986)
      - [Installation from the Snap Store](/t/snapcraft-installation-and-setup/32986#heading--store)
      - [Repository version or snap](/t/snapcraft-installation-and-setup/32986#heading--repository)
      - [Snapcraft LXD and Multipass backends](/t/snapcraft-installation-and-setup/32986#heading--backend)
1. [How Snapcraft builds a snap](/t/how-snapcraft-builds-a-snap/33017)
   - [snapcraft.yaml](/t/how-snapcraft-builds-a-snap/33017#heading--snapcraft)
      - [Main definitions inside snapcraft.yaml](/t/how-snapcraft-builds-a-snap/33017#heading--definitions)
   - [Snapcraft build lifecycle](/t/how-snapcraft-builds-a-snap/33017#heading--build)
   - [Snapcraft build output](/t/how-snapcraft-builds-a-snap/33017#heading--output)
1. [Basic snapcraft.yaml example](/t/basic-snapcraft-yaml-example/33074)
   - [Metadata](/t/basic-snapcraft-yaml-example/33074#heading--metadata)
   - [Base](/t/basic-snapcraft-yaml-example/33074#heading--base)
   - [Confinement](/t/basic-snapcraft-yaml-example/33074#heading--confinement)
     - [Interfaces](/t/basic-snapcraft-yaml-example/33074#heading--interfaces)
   - [Build definition](/t/basic-snapcraft-yaml-example/33074#heading--build)
     - [The parts definition](/t/basic-snapcraft-yaml-example/33074#heading--parts)
     - [The apps definition](/t/basic-snapcraft-yaml-example/33074#heading--apps)
1. [Intermediate snapcraft.yaml example](/t/intermediate-snapcraft-yaml-example/33076)
   - [adopt-info](/t/intermediate-snapcraft-yaml-example/33076#heading--adopt)
   - [grade](/t/intermediate-snapcraft-yaml-example/33076#heading--grade)
   - [architectures](/t/intermediate-snapcraft-yaml-example/33076#heading--architectures)
   - [Build definition](/t/intermediate-snapcraft-yaml-example/33076#heading--build)
     - [The parts definition](/t/intermediate-snapcraft-yaml-example/33076#heading--parts)
     - [The apps definition](/t/intermediate-snapcraft-yaml-example/33076#heading--apps)
 1. [Build and publishing example](/t/build-and-publishing-example/33078)
    - [Snap build process](/t/build-and-publishing-example/33078#heading--build)
    - [Snap publication process](/t/build-and-publishing-example/33078#heading--publish)
    - [Snap Store channels](/t/build-and-publishing-example/33078#heading--channels)
    - [Next steps](/t/build-and-publishing-example/33078#heading--next)