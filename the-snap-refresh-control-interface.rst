.. 26569.md

.. \_the-snap-refresh-control-interface:

The snap-refresh-control interface
==================================

The ``snap-refresh-control`` interface allows extended control, via `snapctl <https://snapcraft.io/docs/using-the-snapctl-tool>`__, of refreshes targeting the snap.

**This interface and the full set of features it requires to function are currently under development.**

[note type=“positive” status=“Interface documentation”]

See `Interface management <interface-management.md>`__ and `Supported interfaces <supported-interfaces.md>`__ for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-snap-refresh-control-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

`Auto-connect <interface-management.md#the-snap-refresh-control-interface-heading--auto-connections>`__: no `Super-privileged <super-privileged-interfaces.md>`__: yes

``snap-refresh-control`` is a marker interface (with no associated AppArmor or Seccomp rules).

Currently it allows connected snaps to execute ``snapctl refresh --proceed`` to unblock pending refreshes outside of the context of the ``gate-auto-refresh`` hook. This interface should be used with caution.

Code examples
-------------

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/snap_refresh_control_test.go

The source code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/snap_refresh_control.go