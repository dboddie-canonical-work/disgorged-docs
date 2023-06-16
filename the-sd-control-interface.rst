.. 25489.md

.. \_the-sd-control-interface:

The sd-control interface
========================

The ``sd-control`` interface allows for the management and control of SD cards on certain devices using the DualSD driver.

[note type=“positive” status=“Interface documentation”]

See `Interface management <interface-management.md>`__ and `Supported interfaces <supported-interfaces.md>`__ for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-sd-control-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

`Auto-connect <interface-management.md#the-sd-control-interface-heading--auto-connections>`__: no `Super-privileged <super-privileged-interfaces.md>`__: yes

The main DualSD device node (``/dev/DualSD``) is used to control certain aspects of SD cards on the system.

Requires snapd version *2.51.3+*.

.. raw:: html

   <h3 id="the-sd-control-interface-heading-code">

Code examples

.. raw:: html

   </h3>

The source code for this interface is in the *snapd* repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/sd_control.go
