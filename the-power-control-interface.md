.. 26506.md

.. _the-power-control-interface:

# The power-control interface

The `power-control` interface allows the reading and setting of system power settings.

This interface is primarily intended to be used with [Ubuntu Core](/t/glossary/14612#heading--ubuntu-core).

[note type="positive" status="Interface documentation"]

See [Interface management](/t/interface-management/6154) and [Supported interfaces](/t/supported-interfaces/7744) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>

**Auto-connect**: no

This interface enables:
- reading of all power settings:
`/sys/devices/**/power/`
- setting wake-up events for supported devices:
`/sys/devices/**/power/wakeup`
- configuring power management for supported devices at runtime:
 `/sys/devices/**/power/control`


### Code examples

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/power_control_test.go

The source code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/power_control.go