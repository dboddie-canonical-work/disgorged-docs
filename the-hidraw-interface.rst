.. 7837.md

.. \_the-hidraw-interface:

The hidraw interface
====================

``hidraw`` enables raw access to USB and Bluetooth Human Interface (*hidraw*) devices. This interface is restricted because it provides privileged access to hardware devices.

**Auto-Connect**: no **Attributes**: - Should specify a single path attribute: \* ``path`` (slot): path to hidraw device node e.g. /dev/hidraw0 - Or three attributes: \* ``usb-vendor`` (slot): integer representing the USB Vendor ID, must be in range 0 < vid <= 65535 \* ``usb-product`` (slot): integer representing the USB Product ID, must be in range 0 <= vid <= 65535 \* ``path`` (slot): path where a symlink will be created to the device e.g. ``/dev/hidraw-mydevice``

To use a hidraw device, the snap developer must add ``plugs: [ hidraw ]`` to a snap’s `snapcraft.yaml <the-snapcraft-yaml-schema.md>`__. The snap user can then access a specific hidraw device with an `interface connection <interface-management.md#the-hidraw-interface-heading--manual-connections>`__.

Use ``snap interface hidraw`` to see which hidraw devices are available on the system.

Once connected, the consuming snap can use the device via the path specified by the connected slot.

   ⓘ This is a snap interface. See `Interface management <interface-management.md>`__ and `Supported interfaces <supported-interfaces.md>`__ for further details on how interfaces are used.
