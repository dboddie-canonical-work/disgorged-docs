.. 7777.md

.. _the-classic-support-interface:

# The classic-support interface

The `classic-support` interface sets special permissions for the [classic snap](https://snapcraft.io/classic), effectively giving device ownership to its connected snaps.

This interface is intended to be used only with [Ubuntu Core](/t/glossary/14612#heading--ubuntu-core).

Requires snapd version _2.23+_.

[note type="positive" status="Interface documentation"]

See [Interface management](/t/interface-management/6154) and [Supported interfaces](/t/supported-interfaces/7744) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>


**[Auto-connect](/t/interface-management/6154#heading--auto-connections)**: no</br>
**[Super-privileged](/t/super-privileged-interfaces/34740)**: yes</br>

### Code examples

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/classic_support_test.go

The source code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/classic_support.go