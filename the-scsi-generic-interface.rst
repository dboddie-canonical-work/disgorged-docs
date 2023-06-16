.. 28409.md

.. _the-scsi-generic-interface:

The scsi-generic interface
==========================

The ``scsi-generic`` interface allows read and write access to `SCSI Generic driver <https://www.kernel.org/doc/html/latest/scsi/scsi-generic.html>`__ (sg) devices.

[note type=“positive” status=“Interface documentation”]

See :ref:`Interface management <interface-management>` and :ref:`Supported interfaces <supported-interfaces>` for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-scsi-generic-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

`Auto-connect <interface-management.md#the-scsi-generic-interface-heading--auto-connections>`__: no

-  ``shared-memory`` (slot and plug):

Code examples
-------------

.. code:: yaml

   apps:
    app:
     command: foo
     plugs: [scsi-generic]

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/scsi_generic_test.go

The source code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/scsi_generic.go
