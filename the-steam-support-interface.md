.. 30990.md

.. _the-steam-support-interface:

# The steam-support interface

The `steam-support` interface has been developed specifically to help Valve's Steam client configure [pressure-vessel](https://gitlab.steamos.cloud/steamrt/steam-runtime-tools/-/tree/master/pressure-vessel) containers from the [Steam snap](https://snapcraft.io/steam).

Only the Steam snap may establish this interface. See [Introducing early access to the Steam snap](https://discourse.ubuntu.com/t/introducing-early-access-to-the-steam-snap/28082) for more details.

[note type="positive" status="Interface documentation"]

See [Interface management](/t/interface-management/6154) and [Supported interfaces](/t/supported-interfaces/7744) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>

**[Auto-connect](/t/interface-management/6154#heading--auto-connections)**: no</br>
**[Super-privileged](/t/super-privileged-interfaces/34740)**: yes</br>


### Code examples

The source code for the Steam snap: https://github.com/canonical/steam-snap

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/steam_support_test.go

The source code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/steam_support.go