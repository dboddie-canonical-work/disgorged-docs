.. 32983.md

.. _snapcraft-quickstart:

Snapcraft quickstart
====================

This quickstart *how-to* will guide you through the steps required to **create**, **build** and **publish** your own **snap package** with the *snapcraft* command line tool.

The purpose of this how-to is to provide Linux developers, packagers, and users with a basic and intermediate knowledge of how to package applications as snaps. It covers the following:

-  an overview of the snap ecosystem
-  a detailed explanation of the Snapcraft tool and its usage
-  the syntax and components of the build recipe for snaps (the *snapcraft.yaml* file)
-  the process of uploading a built snap into the Snap Store

Here’s what you need
--------------------

-  a basic understanding of Linux and the command line
-  `Ubuntu 20.04 LTS <https://releases.ubuntu.com/20.04/>`__, or later, installed
-  10GB of free storage space
-  access to the internet

The above requirements are specific to this tutorial. Other distributions can be used, and other platforms are supported. See `Installing snapd <https://snapcraft.io/docs/installing-snapd>`__ for details.

Step-by-step guide
------------------

1. :ref:`Snapcraft installation and setup <snapcraft-installation-and-setup>`

   -  `Installation from the Snap Store <snapcraft-installation-and-setup.md#snapcraft-quickstart-heading--store>`__
   -  `Repository version or snap <snapcraft-installation-and-setup.md#snapcraft-quickstart-heading--repository>`__
   -  `Snapcraft LXD and Multipass backends <snapcraft-installation-and-setup.md#snapcraft-quickstart-heading--backend>`__

2. :ref:`How Snapcraft builds a snap <how-snapcraft-builds-snaps>`

   -  `snapcraft.yaml <how-snapcraft-builds-snaps.md#snapcraft-quickstart-heading--snapcraft>`__

      -  `Main definitions inside snapcraft.yaml <how-snapcraft-builds-snaps.md#snapcraft-quickstart-heading--definitions>`__

   -  `Snapcraft build lifecycle <how-snapcraft-builds-snaps.md#snapcraft-quickstart-heading--build>`__
   -  `Snapcraft build output <how-snapcraft-builds-snaps.md#snapcraft-quickstart-heading--output>`__

3. :ref:`Basic snapcraft.yaml example <basic-snapcraft-yaml-example>`

   -  `Metadata <basic-snapcraft-yaml-example.md#snapcraft-quickstart-heading--metadata>`__
   -  `Base <basic-snapcraft-yaml-example.md#snapcraft-quickstart-heading--base>`__
   -  `Confinement <basic-snapcraft-yaml-example.md#snapcraft-quickstart-heading--confinement>`__

      -  `Interfaces <basic-snapcraft-yaml-example.md#snapcraft-quickstart-heading--interfaces>`__

   -  `Build definition <basic-snapcraft-yaml-example.md#snapcraft-quickstart-heading--build>`__

      -  `The parts definition <basic-snapcraft-yaml-example.md#snapcraft-quickstart-heading--parts>`__
      -  `The apps definition <basic-snapcraft-yaml-example.md#snapcraft-quickstart-heading--apps>`__

4. :ref:`Intermediate snapcraft.yaml example <intermediate-snapcraft-yaml-example>`

   -  `adopt-info <intermediate-snapcraft-yaml-example.md#snapcraft-quickstart-heading--adopt>`__
   -  `grade <intermediate-snapcraft-yaml-example.md#snapcraft-quickstart-heading--grade>`__
   -  `architectures <intermediate-snapcraft-yaml-example.md#snapcraft-quickstart-heading--architectures>`__
   -  `Build definition <intermediate-snapcraft-yaml-example.md#snapcraft-quickstart-heading--build>`__

      -  `The parts definition <intermediate-snapcraft-yaml-example.md#snapcraft-quickstart-heading--parts>`__
      -  `The apps definition <intermediate-snapcraft-yaml-example.md#snapcraft-quickstart-heading--apps>`__

5. :ref:`Build and publishing example <build-and-publishing-example>`

   -  `Snap build process <build-and-publishing-example.md#snapcraft-quickstart-heading--build>`__
   -  `Snap publication process <build-and-publishing-example.md#snapcraft-quickstart-heading--publish>`__
   -  `Snap Store channels <build-and-publishing-example.md#snapcraft-quickstart-heading--channels>`__
   -  `Next steps <build-and-publishing-example.md#snapcraft-quickstart-heading--next>`__

.. toctree::
   :hidden:

   snapcraft-installation-and-setup
   how-snapcraft-builds-snaps
   basic-snapcraft-yaml-example
   intermediate-snapcraft-yaml-example
   build-and-publishing-example
