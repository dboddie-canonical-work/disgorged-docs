.. 7777.md

.. _the-classic-support-interface:

# The classic-support interface

The `classic-support` interface sets special permissions for the [classic snap](https://snapcraft.io/classic), effectively giving device ownership to its connected snaps.

This interface is intended to be used only with [Ubuntu Core](glossary.md#the-classic-support-interface-heading--ubuntu-core).

Requires snapd version _2.23+_.

[note type="positive" status="Interface documentation"]

See [Interface management](interface-management.md) and [Supported interfaces](supported-interfaces.md) for further details on how interfaces are used.
[/note]

---

<h2 id='the-classic-support-interface-heading--dev-details'>Developer details </h2>


**[Auto-connect](interface-management.md#the-classic-support-interface-heading--auto-connections)**: no</br>
**[Super-privileged](super-privileged-interfaces.md)**: yes</br>

### Code examples

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/classic_support_test.go

The source code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/classic_support.go