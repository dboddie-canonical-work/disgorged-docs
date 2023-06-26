.. 25495.md

.. _the-desktop-launch-interface:

The desktop-launch interface
============================

The ``desktop-launch`` interface allows :ref:`strictly confined <snap-confinement>` snaps to identify and launch desktop applications in (or from) other snaps.

.. note::


          See :ref:`Interface management <interface-management>` and :ref:`Supported interfaces <supported-interfaces>` for further details on how interfaces are used.

--------------


.. _the-desktop-launch-interface-heading--dev-details:

Developer details
-----------------

`Auto-connect <interface-management.md#the-desktop-launch-interface-heading--auto-connections>`__: no :ref:`Super-privileged <super-privileged-interfaces>`: yes

Requires snapd version *2.52+*.


.. _the-desktop-launch-interface-heading-code:

Code examples
~~~~~~~~~~~~~

The source code for this interface is in the *snapd* repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/desktop_launch.go
