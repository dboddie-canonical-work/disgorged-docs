.. 26498.md

.. _the-fpga-interface:

# The fpga interface

The `fpga` interface allows access to the [FPGA subsystem](https://www.kernel.org/doc/html/latest/driver-api/fpga/index.html).

[note type="positive" status="Interface documentation"]

See [Interface management](/t/interface-management/6154) and [Supported interfaces](/t/supported-interfaces/7744) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>

**Auto-connect**: no
**Allow-installation**: yes

Devices:
`/dev/fpga[0-9]* rw,`


### Code examples

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/fpga_test.go

The source code for the interface is in the snapd repository:[https://github.com/snapcore/snapd/blob/master/interfaces/builtin/fpga.go](https://github.com/snapcore/snapd/blob/master/interfaces/builtin/fpga.go)