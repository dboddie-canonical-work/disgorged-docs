.. 26498.md

.. \_the-fpga-interface:

The fpga interface
==================

The ``fpga`` interface allows access to the `FPGA subsystem <https://www.kernel.org/doc/html/latest/driver-api/fpga/index.html>`__.

[note type=“positive” status=“Interface documentation”]

See `Interface management <interface-management.md>`__ and `Supported interfaces <supported-interfaces.md>`__ for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-fpga-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

**Auto-connect**: no **Allow-installation**: yes

Devices: ``/dev/fpga[0-9]* rw,``

Code examples
-------------

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/fpga_test.go

The source code for the interface is in the snapd repository:https://github.com/snapcore/snapd/blob/master/interfaces/builtin/fpga.go