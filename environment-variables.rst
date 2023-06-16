.. 7983.md

.. \_environment-variables:

Environment variables
=====================

Environment variables are widely used across Linux to provide convenient access to system and application properties.

Both `Snapcraft <snapcraft-overview.md>`__ and snapd consume, set, and pass-through specific environment variables to support building and running snaps.

See below for the various environment variables available to snap applications. For environment variables connected to Snapcraft, see `Parts environment variables <parts-environment-variables.md>`__.

Snap specific environment variables
-----------------------------------

List environment variables
~~~~~~~~~~~~~~~~~~~~~~~~~~

Each snap runs in a custom environment specifically made for it. To get an overview of the variables in it, you can open a shell as the snap and run the ``env`` command.

.. code:: bash

   $ snap run --shell <snap>.<command>
   $ env
   XDG_VTNR=1
   SSH_AGENT_PID=5543
   XDG_SESSION_ID=2
   SNAP_USER_COMMON=/home/<user>/snap/<snap>/common
   SNAP_LIBRARY_PATH=/var/lib/snapd/lib/gl:
   SNAP_COMMON=/var/snap/<snap>/common
   [...]

Alongside the many system-specific variables, this environment will include the following:

+---------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| `SNAP <#environment-variables-heading--snap>`__                           | `SNAP_ARCH <#environment-variables-heading--snap-arch>`__                   |
+---------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| `SNAP_COMMON <#environment-variables-heading--snap-common>`__             | `SNAP_DATA <#environment-variables-heading--snap-data>`__                   |
+---------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| `SNAP_EUID <#environment-variables-heading--snap-euid>`__                 | `SNAP_INSTANCE_NAME <#environment-variables-heading--snap-instance-name>`__ |
+---------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| `SNAP_INSTANCE_KEY <#environment-variables-heading--snap-instance-key>`__ | `SNAP_LIBRARY_PATH <#environment-variables-heading--snap-library-path>`__   |
+---------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| `SNAP_NAME <#environment-variables-heading--name>`__                      | `SNAP_REAL_HOME <#environment-variables-heading--snap-real-home>`__         |
+---------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| `SNAP_REVISION <#environment-variables-heading--snap-revision>`__         | `SNAP_SAVE_DATA <#environment-variables-heading--snap-save-data>`__         |
+---------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| `SNAP_UID <#environment-variables-heading--snap-uid>`__                   | `SNAP_USER_COMMON <#environment-variables-heading--snap-user-common>`__     |
+---------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| `SNAP_USER_DATA <#environment-variables-heading--snap-user-data>`__       | `SNAP_VERSION <#environment-variables-heading--snap-version>`__             |
+---------------------------------------------------------------------------+-----------------------------------------------------------------------------+
| `HOME <#environment-variables-heading--home>`__                           | `PATH <#environment-variables-heading--path>`__                             |
+---------------------------------------------------------------------------+-----------------------------------------------------------------------------+

.. raw:: html

   <h3 id="environment-variables-heading--snap">

.. raw:: html

   <pre>SNAP</pre>

.. raw:: html

   </h3>

Directory where the snap is mounted. This is where all the files in your snap are visible in the filesystem. All of the data in the snap is read-only and cannot be changed.

Typical value: ``/snap/hello-world/27``

.. raw:: html

   <h3 id="environment-variables-heading--snap-arch">

.. raw:: html

   <PRE>SNAP_ARCH</PRE>

.. raw:: html

   </h3>

CPU architecture of the running system.

Typical value ``amd64``

Other values are: ``i386``, ``armhf``, ``arm64``.

.. raw:: html

   <h3 id="environment-variables-heading--snap-common">

.. raw:: html

   <pre>SNAP_COMMON</pre>

.. raw:: html

   </h3>

Directory for system data that is common across revisions of a snap.

This directory is owned and writable by ``root`` and is meant to be used by background applications (daemons, services). Unlike ``SNAP_DATA`` this directory **is not** backed up and restored across snap refresh and revert operations.

Typical value: ``/var/snap/hello-world/common``

.. raw:: html

   <h3 id="environment-variables-heading--snap-data">

.. raw:: html

   <pre>SNAP_DATA</pre>

.. raw:: html

   </h3>

Directory for system data of a snap.

This directory is owned and writable by ``root`` and is meant to be used by background applications (daemons, services). Unlike ``SNAP_COMMON`` this directory is backed up and restored across ``snap refresh`` and ``snap revert`` operations.

Typical value ``/var/snap/hello-world/27``

.. raw:: html

   <h3 id="environment-variables-heading--snap-euid">

.. raw:: html

   <pre>SNAP_EUID</pre>

.. raw:: html

   </h3>

This variable contains the *effective* user ID (euid) of the user running the snap instance. See also `SNAP_UID <#environment-variables-heading--snap-uid>`__.

For this variable to be exposed by a snap, the snap developer will need to include the following ```assumes`` <snapcraft-top-level-metadata.md#environment-variables-heading--assumes>`__ value:

.. code:: yaml

   assumes: [snap-uid-envvars]

Requires *snapd* 2.59+.

.. raw:: html

   <h3 id="environment-variables-heading--snap-instance-name">

.. raw:: html

   <pre>SNAP_INSTANCE_NAME</pre>

.. raw:: html

   </h3>

The name of snap instance, including instance key if one is set (snapd 2.36+).

For example snap ``hello-world`` with instance key ``foo`` has instance name equal to ``hello-world_foo``.

Typical value: ``hello-world``

.. raw:: html

   <h3 id="environment-variables-heading--snap-instance-key">

.. raw:: html

   <pre>SNAP_INSTANCE_KEY</pre>

.. raw:: html

   </h3>

Instance key if one was set during installation or empty (snapd 2.36+).

For example instance ``hello-world_foo`` has an instance key ``foo``.

Typical value: none

.. raw:: html

   <h3 id="environment-variables-heading--snap-library-path">

.. raw:: html

   <pre>SNAP_LIBRARY_PATH</pre>

.. raw:: html

   </h3>

Directory with additional system libraries. This variable is used internally by snapcraft.

The value is always ``/var/lib/snapd/lib/gl:`` Please note the colon at the end of that value, the variable is a colon-separated list.

The referenced directory is typically empty unless Nvidia proprietary drivers are in use.

.. raw:: html

   <h3 id="environment-variables-heading--snap-name">

.. raw:: html

   <pre>SNAP_NAME</pre>

.. raw:: html

   </h3>

The name of the snap as specified in the ``snapcraft.yaml`` file.

Typical value: ``hello-world``

.. raw:: html

   <h3 id="environment-variables-heading--snap-real-home">

.. raw:: html

   <pre>SNAP_REAL_HOME</pre>

.. raw:: html

   </h3>

The vanilla ``HOME`` environment variable before snapd-induced remapping, refer `Any way to acquire the originally set ``HOME`` environment variable? - snapcraft - snapcraft.io <https://snapcraft.io/docs/any-way-to-acquire-the-originally-set-home-environment-variable>`__ for more info.

Available `since snapd 2.46 <https://github.com/snapcore/snapd/pull/9189/commits/37d0a229>`__.

.. raw:: html

   <h3 id="environment-variables-heading--snap-revision">

.. raw:: html

   <pre>SNAP_REVISION</pre>

.. raw:: html

   </h3>

Revision of the snap, as allocated by the Snap Store on upload or as allocated by snapd for locally installed snaps.

The Snap Store assigns monotonic revisions to each upload of a given snap. Snapd uses Snap Store revisions if accompanying assertions are available or uses a locally generated number. Locally generated numbers are prefixed with ``x`` to distinguish them from Snap Store uploads.

Typical value: ``27`` or ``x1``

.. raw:: html

   <h3 id="environment-variables-heading--snap-save-data">

.. raw:: html

   <pre>SNAP_SAVE_DATA</pre>

.. raw:: html

   </h3>

This variable is only exposed on `Ubuntu Core <glossary.md#environment-variables-heading--ubuntu-core>`__ systems, and was introduced with snapd 2.57.

It points to a snap-specific location on the ubuntu-save partition where the snap is allowed to store persistent files (like certificates or configuration files) that will survive a `factory reset <https://ubuntu.com/core/docs/recovery-modes#environment-variables-heading--factory>`__ of the Ubuntu Core device.

See `ubuntu-save <https://ubuntu.com/core/docs/storage-layout#environment-variables-heading--save>`__ in the Ubuntu Core documentation for more details on storage layout with this specific partition.

.. raw:: html

   <h3 id="environment-variables-heading--snap-uid">

.. raw:: html

   <pre>SNAP_UID</pre>

.. raw:: html

   </h3>

This variable contains the user ID (uid) of the user running this snap instance. See also `SNAP_EUID <#environment-variables-heading--snap-euid>`__.

For this variable to be exposed by a snap, the snap developer will need to include the following ```assumes`` <snapcraft-top-level-metadata.md#environment-variables-heading--assumes>`__ value:

.. code:: yaml

   assumes: [snap-uid-envvars]

Requires *snapd* 2.59+.

.. raw:: html

   <h3 id="environment-variables-heading--snap-user-common">

.. raw:: html

   <pre>SNAP_USER_COMMON</pre>

.. raw:: html

   </h3>

Directory for user data that is common across revisions of a snap.

Unlike ``SNAP_DATA``, data present in this directory is not backed up or restored across ``snap refresh`` and ``snap revert`` operations. The directory is suitable for large data that the application can access even if it was made or modified by a future version of a snap.

Typical value ``/home/zyga/snap/hello-world/common``

.. raw:: html

   <h3 id="environment-variables-heading--snap-user-data">

.. raw:: html

   <pre>SNAP_USER_DATA</pre>

.. raw:: html

   </h3>

Directory for user data.

This directory is backed up and restored across ``snap refresh`` and ``snap revert`` operations.

Typical value: ``/home/zyga/snap/hello-world/27``

The final number there is ``$SNAP_REVISION``.

.. raw:: html

   <h3 id="environment-variables-heading--snap-version">

.. raw:: html

   <pre>SNAP_VERSION</pre>

.. raw:: html

   </h3>

The version string as specified in the ``snapcraft.yaml``

Typical value ``6.3``

Generic variables
-----------------

.. raw:: html

   <h3 id="environment-variables-heading--home">

.. raw:: html

   <pre>HOME</pre>

.. raw:: html

   </h3>

For non-classic snaps, this environment variable is re-written to ``SNAP_USER_DATA`` by snapd so that each snap appears to have a dedicated home directory that is a subdirectory of the real home directory.

For classic confinement snaps, the value remains unchanged.

Typical value: ``/home/_user_name_/snap/_snap_name_/_snap_revision_`` (e.g. ``/home/zyga/snap/hello-world/27``)

.. raw:: html

   <h3 id="environment-variables-heading--path">

.. raw:: html

   <pre>PATH</pre>

.. raw:: html

   </h3>

This environment variable is re-written by snapd so that it is consistent with the view of the filesystem presented to snap applications.

The value is always:

-  For non-classic confinement snaps:

   ::

      $SNAP/usr/sbin:$SNAP/usr/bin:$SNAP/sbin:$SNAP/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

-  For classic confinement snaps: ``/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games``
