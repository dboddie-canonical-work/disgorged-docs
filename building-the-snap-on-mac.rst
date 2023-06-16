.. 6751.md

.. _building-the-snap-on-mac:

Building the snap on Mac
========================

[quote] **NOTE TO EDITORS**

This topic contributes to a new set of snap documentation. See `Proposed new documentation outline <https://snapcraft.io/docs/proposed-new-documentation-outline-page-deprecated>`__ for further details.

[/quote]

Now that you have a :ref:`snapcraft.yaml <creating-a-snap>` describing how to assemble your app and dependencies, you can build a snap.

Snapcraft, the command-line tool for building snaps, is distributed using Homebrew on the Mac. Be sure to `install Homebrew <https://brew.sh/>`__ before continuing.

Next, install snapcraft:

.. code:: bash

   brew install snapcraft

[quote] ⚠ The remainder of these steps depend upon functionality landing in October 2018. Prior to this, you can use :ref:`Docker <building-the-snap-on-docker>` to build snaps on Mac. [/quote]

Return to the root directory of the project containing your snapcraft.yaml and run snapcraft:

.. code:: bash

   snapcraft

[quote] ⓘ If you are working with an Electron app, you will use the snapcraft tool for publishing to the Snap Store but not for building your snap. Electron apps do not have a snapcraft.yaml file.

:ref:`Follow this guide <electron-apps>` to build a snap of an Electron app using electron-builder. [/quote]

If the snap build completes successfully, you will find a ``.snap`` file in the same directory that you ran the snapcraft command. You can inspect its contents to ensure it contains all of your application’s assets:

::

   unsquashfs -l *.snap

Next steps
----------

Continue on to learn how to install, test, and publish your snap file.
