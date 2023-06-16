.. 25485.md

.. _the-netlink-driver-interface:

# The netlink-driver interface

The `netlink-driver` interface allows a kernel module to expose itself to user-space via the Netlink protocol, typically to transfer information between the kernel and user-space processes.

See also [netlink-audit](the-netlink-audit-interface.md) and [netlink-connector](the-netlink-connector-interface.md).

[note type="positive" status="Interface documentation"]

See [Interface management](interface-management.md) and [Supported interfaces](supported-interfaces.md) for further details on how interfaces are used.
[/note]

---

<h2 id='the-netlink-driver-interface-heading--dev-details'>Developer details </h2>

**Auto-connect**: no

Further confinement for particular families/protocols is implemented via Seccomp filtering network Netlink.

Requires snapd version _2.51.1+_.

<h3 id='the-netlink-driver-interface-heading-code'>Code examples</h3>

The source code for this interface is in the *snapd* repository:
<https://github.com/snapcore/snapd/blob/master/interfaces/builtin/netlink_driver.go>