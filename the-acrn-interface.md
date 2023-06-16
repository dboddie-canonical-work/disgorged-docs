.. 30982.md

.. _the-acrn-interface:

# The acrn interface

The `acrn` interface  allows access to, and control of, user virtual machines using the [ACRN hypervisor](https://projectacrn.org/).

**This interface is primarily intended to be used with [Ubuntu Core](glossary.md#heading--ubuntu-core) devices.**

[note type="positive" status="Interface documentation"]

See [Interface management](interface-management.md) and [Supported interfaces](supported-interfaces.md) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>

**[Auto-connect](interface-management.md#heading--auto-connections)**: no</br>
**[Super-privileged](the-interface-auto-connection-mechanism.md#heading--super)**: no</br>

### Code examples

The following (third-party) repository contains recipes to create snap packages for ACRN: https://github.com/gvancuts/acrn-snap

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/acrn_support_test.go

The source code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/acrn_support.go