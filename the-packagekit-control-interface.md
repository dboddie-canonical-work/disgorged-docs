.. 13052.md

.. _the-packagekit-control-interface:

# The packagekit-control interface

`packagekit-control` allows control of the [PackageKit](https://www.freedesktop.org/software/PackageKit/) service, giving privileged access to native package management on the system.

This interface is intended to work in tandem with [the AppStream interface](the-appstream-metadata-interface.md). Snaps distributed via the public [Snap store](https://snapcraft.io/store) are not typically granted auto-connection for this interface.

**[Auto-connect](interface-management.md#heading--auto-connections)**: no</br>
**[Super-privileged](super-privileged-interfaces.md)**: yes</br>

Requires snapd version _2.41+_.`

> ⓘ  This is a snap interface. See [Interface management](interface-management.md) and [Supported interfaces](supported-interfaces.md) for further details on how interfaces are used.