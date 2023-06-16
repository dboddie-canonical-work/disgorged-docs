.. 7879.md

.. \_the-netlink-connector-interface:

The netlink-connector interface
===============================

The ``netlink-connector`` interface allows communication through the kernel Netlink connector.

See also `netlink-driver <the-netlink-driver-interface.md>`__ and `netlink-audit <the-netlink-audit-interface.md>`__.

[note type=“positive” status=“Interface documentation”]

See `Interface management <interface-management.md>`__ and `Supported interfaces <supported-interfaces.md>`__ for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-netlink-connector-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

**Auto-connect**: no

As NETLINK_CONNECTOR is not finely mediated and app-specific, use of this interface allows communications via all Netlink connectors. See `Kernel connector <https://www.kernel.org/doc/Documentation/connector/connector.txt>`__ (on kernel.org) for further details.

Requires snapd version *2.26+*.

.. raw:: html

   <h3 id="the-netlink-connector-interface-heading-code">

Code examples

.. raw:: html

   </h3>

The snap of the `usbtop <>`__ kernel module, used to monitor the bandwidth of USB buses and devices, uses the *netlink-audit* interface: `https://github.com/ogra1/usbtop/blob/master/snap/snapcraft.yaml <https://github.com/ogra1/usbtop/blob/3743b5a55e6df70e6dd95292121279f1013ba570/snap/snapcraft.yaml#L50>`__

The source code for this interface is in the *snapd* repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/netlink_connector.go