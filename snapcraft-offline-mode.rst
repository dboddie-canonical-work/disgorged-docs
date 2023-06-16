.. 27547.md

.. \_snapcraft-offline-mode:

Snapcraft offline mode
======================

By default, Snapcraft requires network connectivity to both source the Multipass or LXD images used to host the build environment, and to populate the build environment with whatever dependencies, source repositories, binaries, and other packages that are required to build the snap.

It may sometimes be necessary, or helpful, to build snaps without this network dependency, such as when needing *Aeroplane mode* on a laptop, or in areas with restricted bandwidth. For those situations, Snapcraft 6.x has an experimental offline mode.

-  `Preparation <#snapcraft-offline-mode-heading--preparation>`__
-  `Run snapcraft offline <#snapcraft-offline-mode-heading--offline>`__

[note type=“caution” status=“Only works with Snapcraft 6.x”]

Offline mode is considered **experimental** and only works with Snapcraft 6.x. It will not work with earlier versions, or Snapcraft 7.x. [/note]

--------------

.. raw:: html

   <h2 id="snapcraft-offline-mode-heading--preparation">

Preparation

.. raw:: html

   </h2>

Before using Snapcraft’s offline mode, the build environment needs to be populated with everything necessary to build the snap.

This requirement is the equivalent of running the build process up to and including the *pull* stage of the `Parts lifecycle <parts-lifecycle.md>`__, and with a network connection, this can be accomplished from within a pre-prepared `snapcraft <snapcraft-overview.md>`__ project directory with the ``snapcraft pull`` command:

.. code:: bash

   $ snapcraft pull
   Pulling [...]

With the pull stage complete, everything the snap depends upon to build is now locally cached.

.. raw:: html

   <h2 id="snapcraft-offline-mode-heading--offline">

Run snapcraft offline

.. raw:: html

   </h2>

To start the offline build process, add the ``--offline`` argument to the *snapcraft* command:

.. code:: bash

   $ snapcraft --offline
   *EXPERIMENTAL* --offline enabled.
   Launching a container.
   [...]
   Building...
   Staging...
   Priming...
   Snapping...

Snapcraft will now build the snap without requiring a network connection, using the data cached from the pull stage.

In offline mode, the snapcraft.yaml for the snap can still be edited, and the snap rebuilt, as long as an edit doesn’t result in additional packages being required. Another consideration is that cached dependencies can become outdated.

To update the cache and add any new missing dependencies, rerun the ``snapcraft pull`` command with a network connection.

The ``-offline`` argument can also be used while connected to the network. In its current *experimental* implementation, Snapcraft will re-order the build process to perform an initial download and cache step for the entire snap without requiring a *snapcraft pull* command.

To learn more about other ways of building snaps with Snapcraft, see `Build options <build-options.md>`__.
