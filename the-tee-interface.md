.. 26573.md

.. _the-tee-interface:

# The tee interface

The `tee` interface  permits access to Trusted Execution Environment (TEE) devices via the [TEE subsystem](https://www.kernel.org/doc/html/latest/staging/tee.html) in the Linux kernel.


This interface is primarily intended to be used with [Ubuntu Core](glossary.md#heading--ubuntu-core).

[note type="positive" status="Interface documentation"]

See [Interface management](interface-management.md) and [Supported interfaces](supported-interfaces.md) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>

**[Auto-connect](interface-management.md#heading--auto-connections)**: no</br>
**[Super-privileged](super-privileged-interfaces.md)**: yes</br>

Intended for snaps needing to access the the TEE subsystem over `/dev/tee[0-9]*`, `/dev/teepriv[0-0]*` or  the Qualcomm equivalent _qseecom_  (Qualcomm Secure Execution Environment Communicator) at `/dev/qseecom`.

### Code examples

The official [Ubuntu Core gadget snap](https://github.com/kubiko/imx8m-gadget) for the [i.MX8M Mini Evaluation Kit](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-mini-applications-processor:8MMINILPD4-EVK) uses this interface: https://github.com/kubiko/imx8m-gadget/blob/imx8mm-evk/snap/snapcraft.yaml

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/tee_test.go

The source code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/tee.go