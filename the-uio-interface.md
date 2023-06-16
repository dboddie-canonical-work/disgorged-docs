.. 16041.md

.. _the-uio-interface:

# The uio interface

`uio` provides access to a specific uio device. This interface is restricted because it provides privileged access to uio hardware.

The slot is intended to be implemented by a gadget snap and is not provided by the core system snap.

**Auto-Connect**: no
**Attributes**:
 * `path` (slot): path to uio device. e.g. `/dev/uio1`

Requires snapd version *2.44+*.

To use the uio device, the snap developer must add `plugs: [ uio ]` to a snap's [snapcraft.yaml](the-snapcraft-yaml-schema.md). The snap user can then access a specific disk partition with an [interface connection](interface-management.md#heading--manual-connections).

Use  `snap interface uio` to see which disk partitions are available on the system for snaps to use:

```bash
$ snap interface uio
name:    uio
summary: allows access to specific uio device
slots:
  - foo:uio1
  - foo:uio2
```

Once connected, the consuming snap can use the device via the path specified by the connected slot.

> ⓘ  This is a snap interface. See [Interface management](interface-management.md) and [Supported interfaces](supported-interfaces.md) for further details on how interfaces are used.