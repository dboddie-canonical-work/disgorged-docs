.. 7838.md

.. \_the-home-interface:

The home interface
==================

The ``home`` `interface <interface-management.md>`__ allows access to non-hidden files owned by the user in the user’s home ($HOME) directory where a user normally stores their personal files and documents.

The majority of snaps use `strict confinement <snap-confinement.md>`__ and do not have arbitrary access a system’s resources, including file and directories in the */home* directory. Without this access, *home* will not be visible in file requesters, or as a destination from within the snap application.

To check whether a snap can connect to $HOME, use the *snap connections* command:

.. code:: bash

   $ snap connections <snap-name>
   Interface  Plug                Slot         Notes
   home       <snap-name>:home    -        -

The above output shows that ``<snap-name>`` does provide a home interface (in the *Plug* column), but that it’s not connected to any slot (denoted by the ``-`` in the slot column).

Use the *snap connect* command to connect an interface:

.. code:: bash

   $ snap connect <snap-name>:home :home

The ``:home`` slot, with no <snap-name> before the colon (``:``) is equivalent to directing the plug to connect to the system, which in this case is the $HOME directory.

A snap developer can `request permission <permission-requests.md>`__ to have the ``home`` interface connected automatically. In this case, non-hidden files and directories will be accessible from that snap without any further configuration being necessary.

Requires snapd version *2.33+*.

[note type=“positive” status=“Interface documentation”]

This is a snap interface. See `Interface management <interface-management.md>`__ and `Supported interfaces <supported-interfaces.md>`__ for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-home-interface-heading--dev">

Developer details

.. raw:: html

   </h2>

`Auto-Connect <the-interface-auto-connection-mechanism.md#the-home-interface-heading--autoconnect>`__: - **yes** on traditional distributions - **no** on all other systems, including `Ubuntu Core <glossary.md#the-home-interface-heading--ubuntu-core>`__

**Transitional**: yes **Attributes**: \* ``read`` (plug): optional, when set to ‘all’, also allows reading non-hidden files in the home directories of all users as traditional file permissions allow. *When set to ‘all’ this plug becomes non-autoconnect.*

Example snaps
-------------

`OBS Studio <https://github.com/snapcrafters/obs-studio>`__: `snapcraft.yaml <https://github.com/snapcrafters/obs-studio/blob/master/snap/snapcraft.yaml>`__ `Signal Desktop <https://github.com/snapcrafters/signal-desktop>`__: `snapcraft.yaml <https://github.com/snapcrafters/signal-desktop/blob/master/snap/snapcraft.yaml>`__

Interface source code
---------------------

`snapd/home.go at master · snapcore/snapd <https://github.com/snapcore/snapd/blob/master/interfaces/builtin/home.go>`__