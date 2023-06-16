.. 25491.md

.. _the-dsp-interface:

The dsp interface
=================

The ``dsp`` interface allows for the control of digital signal processors (DSPs) on specific devices and systems (such as specific *Ambarella* devices)

[note type=“positive” status=“Interface documentation”]

See :ref:`Interface management <interface-management>` and :ref:`Supported interfaces <supported-interfaces>` for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-dsp-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

**Auto-connect**: no

This interface allows privileged access to hardware and kernel drivers related to the digital signal processor and thus is only allowed on specific devices providing the slot via a gadget and is also not auto-connected.

Requires snapd version *2.51+*.

.. raw:: html

   <h3 id="the-dsp-interface-heading-code">

Code examples

.. raw:: html

   </h3>

The source code for this interface is in the *snapd* repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/dsp.go
