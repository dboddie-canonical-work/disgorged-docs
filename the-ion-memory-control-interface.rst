.. 26502.md

.. \_the-ion-memory-control-interface:

The ion-memory-control interface
================================

The ``ion-memory-control`` interface allows access to the Android ION memory allocator, a Linux kernel feature for managing one or more memory pools.

This interface is primarily intended to be used with `Ubuntu Core <glossary.md#the-ion-memory-control-interface-heading--ubuntu-core>`__.

[note type=“positive” status=“Interface documentation”]

See `Interface management <interface-management.md>`__ and `Supported interfaces <supported-interfaces.md>`__ for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-ion-memory-control-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

`Auto-connect <interface-management.md#the-ion-memory-control-interface-heading--auto-connections>`__: no `Super-privileged <super-privileged-interfaces.md>`__: yes

The device is expected in the following location: - ``/dev/ion``

Code examples
-------------

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/ion_memory_control_test.go

The source code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/ion_memory_control.go