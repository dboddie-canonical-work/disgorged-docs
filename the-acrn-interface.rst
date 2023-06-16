.. 30982.md

.. \_the-acrn-interface:

The acrn interface
==================

The ``acrn`` interface allows access to, and control of, user virtual machines using the `ACRN hypervisor <https://projectacrn.org/>`__.

**This interface is primarily intended to be used with**\ `Ubuntu Core <glossary.md#the-acrn-interface-heading--ubuntu-core>`__\ **devices.**

[note type=“positive” status=“Interface documentation”]

See `Interface management <interface-management.md>`__ and `Supported interfaces <supported-interfaces.md>`__ for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-acrn-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

`Auto-connect <interface-management.md#the-acrn-interface-heading--auto-connections>`__: no `Super-privileged <the-interface-auto-connection-mechanism.md#the-acrn-interface-heading--super>`__: no

Code examples
-------------

The following (third-party) repository contains recipes to create snap packages for ACRN: https://github.com/gvancuts/acrn-snap

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/acrn_support_test.go

The source code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/acrn_support.go