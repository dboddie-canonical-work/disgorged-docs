.. 25489.md

.. _the-sd-control-interface:

# The sd-control interface

The `sd-control` interface allows for the management and control of SD cards on certain devices using the DualSD driver.

[note type="positive" status="Interface documentation"]

See [Interface management](interface-management.md) and [Supported interfaces](supported-interfaces.md) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>

**[Auto-connect](interface-management.md#heading--auto-connections)**: no</br>
**[Super-privileged](super-privileged-interfaces.md)**: yes</br>

The main DualSD device node (`/dev/DualSD`) is used to control certain aspects of SD cards on the system.

Requires snapd version _2.51.3+_.

<h3 id='heading-code'>Code examples</h3>

The source code for this interface is in the *snapd* repository:
<https://github.com/snapcore/snapd/blob/master/interfaces/builtin/sd_control.go>