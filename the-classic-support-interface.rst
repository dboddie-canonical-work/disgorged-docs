.. 7777.md

.. _the-classic-support-interface:

The classic-support interface
=============================

The ``classic-support`` interface sets special permissions for the `classic snap <https://snapcraft.io/classic>`__, effectively giving device ownership to its connected snaps.

This interface is intended to be used only with `Ubuntu Core <glossary.md#the-classic-support-interface-heading--ubuntu-core>`__.

Requires snapd version *2.23+*.

[note type=“positive” status=“Interface documentation”]

See :ref:`Interface management <interface-management>` and :ref:`Supported interfaces <supported-interfaces>` for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-classic-support-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

`Auto-connect <interface-management.md#the-classic-support-interface-heading--auto-connections>`__: no :ref:`Super-privileged <super-privileged-interfaces>`: yes

Code examples
-------------

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/classic_support_test.go

The source code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/classic_support.go
