.. 25485.md

.. \_the-netlink-driver-interface:

The netlink-driver interface
============================

The ``netlink-driver`` interface allows a kernel module to expose itself to user-space via the Netlink protocol, typically to transfer information between the kernel and user-space processes.

See also `netlink-audit <the-netlink-audit-interface.md>`__ and `netlink-connector <the-netlink-connector-interface.md>`__.

[note type=“positive” status=“Interface documentation”]

See `Interface management <interface-management.md>`__ and `Supported interfaces <supported-interfaces.md>`__ for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-netlink-driver-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

**Auto-connect**: no

Further confinement for particular families/protocols is implemented via Seccomp filtering network Netlink.

Requires snapd version *2.51.1+*.

.. raw:: html

   <h3 id="the-netlink-driver-interface-heading-code">

Code examples

.. raw:: html

   </h3>

The source code for this interface is in the *snapd* repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/netlink_driver.go