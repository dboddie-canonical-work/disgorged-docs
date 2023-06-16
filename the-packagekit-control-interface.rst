.. 13052.md

.. \_the-packagekit-control-interface:

The packagekit-control interface
================================

``packagekit-control`` allows control of the `PackageKit <https://www.freedesktop.org/software/PackageKit/>`__ service, giving privileged access to native package management on the system.

This interface is intended to work in tandem with `the AppStream interface <the-appstream-metadata-interface.md>`__. Snaps distributed via the public `Snap store <https://snapcraft.io/store>`__ are not typically granted auto-connection for this interface.

`Auto-connect <interface-management.md#the-packagekit-control-interface-heading--auto-connections>`__: no `Super-privileged <super-privileged-interfaces.md>`__: yes

Requires snapd version *2.41+*.\`

   ⓘ This is a snap interface. See `Interface management <interface-management.md>`__ and `Supported interfaces <supported-interfaces.md>`__ for further details on how interfaces are used.
