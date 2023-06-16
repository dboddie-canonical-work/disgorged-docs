.. 25495.md

.. _the-desktop-launch-interface:

# The desktop-launch interface

The `desktop-launch` interface allows [strictly confined](snap-confinement.md) snaps to identify and launch desktop applications in (or from) other snaps.

[note type="positive" status="Interface documentation"]

See [Interface management](interface-management.md) and [Supported interfaces](supported-interfaces.md) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>

**[Auto-connect](interface-management.md#heading--auto-connections)**: no</br>
**[Super-privileged](super-privileged-interfaces.md)**: yes</br>


Requires snapd version _2.52+_.

<h3 id='heading-code'>Code examples</h3>

The source code for this interface is in the *snapd* repository:
<https://github.com/snapcore/snapd/blob/master/interfaces/builtin/desktop_launch.go>