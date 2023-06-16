.. 9720.md

.. _the-adb-support-interface:

The adb-support interface
=========================

``adb-support`` allows a snap to operating the Android Debug Bridge service, providing privileged access to an Android device.

.. raw:: html

   <h2 id="the-adb-support-interface-heading--example">

Example

.. raw:: html

   </h2>

`guiscrcpy <https://snapcraft.io/guiscrcpy>`__ uses *adb-support* to help share an Android screen on a Linux desktop.

[note type=“positive” status=“Interface documentation”]

See :ref:`Interface management <interface-management>` and :ref:`Supported interfaces <supported-interfaces>` for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-adb-support-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

**Auto-connect**: no

Requires snapd version *2.36+*.

.. raw:: html

   <h3 id="the-adb-support-interface-heading-code">

Code examples

.. raw:: html

   </h3>

The adb-support interface is used in the *guiscrcpy* snap: https://github.com/srevinsaju/guiscrcpy/blob/master/snap/snapcraft.yaml

The source code for this interface is in the *snapd* repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/adb_support.go
