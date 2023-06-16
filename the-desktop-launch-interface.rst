.. 25495.md

.. \_the-desktop-launch-interface:

The desktop-launch interface
============================

The ``desktop-launch`` interface allows `strictly confined <snap-confinement.md>`__ snaps to identify and launch desktop applications in (or from) other snaps.

[note type=“positive” status=“Interface documentation”]

See `Interface management <interface-management.md>`__ and `Supported interfaces <supported-interfaces.md>`__ for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-desktop-launch-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

`Auto-connect <interface-management.md#the-desktop-launch-interface-heading--auto-connections>`__: no `Super-privileged <super-privileged-interfaces.md>`__: yes

Requires snapd version *2.52+*.

.. raw:: html

   <h3 id="the-desktop-launch-interface-heading-code">

Code examples

.. raw:: html

   </h3>

The source code for this interface is in the *snapd* repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/desktop_launch.go