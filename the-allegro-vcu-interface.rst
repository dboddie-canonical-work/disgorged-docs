.. 26452.md

.. _the-allegro-vcu-interface:

The allegro-vcu interface
=========================

The ``allegro-vcu`` interface enables access to the Allegro Video Core Unit, using a kernel module which directly controls hardware on the device.

This interface is intended primarily to be used with `Ubuntu Core <glossary.md#the-allegro-vcu-interface-heading--ubuntu-core>`__.

.. note::


          See :ref:`Interface management <interface-management>` and :ref:`Supported interfaces <supported-interfaces>` for further details on how interfaces are used.

--------------

.. raw:: html

   <h2 id="the-allegro-vcu-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

**Auto-connect**: no

Xilinx offers IP for their devices to decode/encode video streams, by using ``/dev/allegroDecodeIP`` and ``/dev/allegroIP`` devices.

These operations should be considered privileged since the driver assumes trusted input, therefore require manual connection.

Code examples
-------------

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/allegro_vcu_test.go

The source code for the interface is in the snapd repository:https://github.com/snapcore/snapd/blob/master/interfaces/builtin/allegro_vcu.go
