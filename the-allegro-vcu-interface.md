.. 26452.md

.. _the-allegro-vcu-interface:

# The allegro-vcu interface

The `allegro-vcu` interface enables access to the Allegro Video Core Unit, using a kernel module which directly controls hardware on the device.

This interface is intended primarily to be used with [Ubuntu Core](/t/glossary/14612#heading--ubuntu-core).

[note type="positive" status="Interface documentation"]

See [Interface management](/t/interface-management/6154) and [Supported interfaces](/t/supported-interfaces/7744) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>

**Auto-connect**: no

Xilinx offers IP for their devices to decode/encode video streams, by using `/dev/allegroDecodeIP` and `/dev/allegroIP` devices.

These operations should be considered privileged since the driver assumes trusted input, therefore require manual connection.

### Code examples

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/allegro_vcu_test.go

The source code for the interface is in the snapd repository:[ https://github.com/snapcore/snapd/blob/master/interfaces/builtin/allegro_vcu.go](https://github.com/snapcore/snapd/blob/master/interfaces/builtin/allegro_vcu.go)