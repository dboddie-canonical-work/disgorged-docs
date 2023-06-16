.. 25495.md

.. _the-desktop-launch-interface:

# The desktop-launch interface

The `desktop-launch` interface allows [strictly confined](/t/snap-confinement/6233) snaps to identify and launch desktop applications in (or from) other snaps.

[note type="positive" status="Interface documentation"]

See [Interface management](/t/interface-management/6154) and [Supported interfaces](/t/supported-interfaces/7744) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>

**[Auto-connect](/t/interface-management/6154#heading--auto-connections)**: no</br>
**[Super-privileged](/t/super-privileged-interfaces/34740)**: yes</br>


Requires snapd version _2.52+_.

<h3 id='heading-code'>Code examples</h3>

The source code for this interface is in the *snapd* repository:
<https://github.com/snapcore/snapd/blob/master/interfaces/builtin/desktop_launch.go>