.. 20116.md

.. \_the-uinput-interface:

The uinput interface
====================

``uinput`` allows write access to ``/dev/uinput`` on the host system for emulating input devices from userspace that can send input events (such as a joystick).

By design, the ``/dev/uinput`` device allows for arbitrary input injection and its default permissions are the standard ``root:root 0660`` across Linux distributions.

Third-party software sometimes installs *udev* rules that change the ``/dev/uinput`` device permissions to world-writable permissions (``0666``) as a shortcut to allow all system users access.

However, *snapd* considers world-writable permissions for ``/dev/uinput`` to be unsafe for most systems because it potentially allows any user with access to the device the ability to inject input events into the kernel.

This means snapd does not install additional *udev* rules to modify device permissions on behalf of snaps, and consequently, will not interfere with the permissions set by third-party software. As a result, snaps that use this interface will have the same ``/dev/uinput`` access as other processes on the system.

See `the joystick interface <the-joystick-interface.md>`__ and `the raw-usb interface <the-raw-usb-interface.md>`__ for potential alternatives.

`Auto-connect <interface-management.md#the-uinput-interface-heading--auto-connections>`__: no `Super-privileged <super-privileged-interfaces.md>`__: yes

Requires snapd version *2.46+* .

   ⓘ This is a snap interface. See `Interface management <interface-management.md>`__ and `Supported interfaces <supported-interfaces.md>`__ for further details on how interfaces are used.
