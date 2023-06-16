.. 26501.md

.. _the-hugepages-control-interface:

# The hugepages-control interface

The `hugepages-control` interface allows controlling [HugePages](https://www.kernel.org/doc/Documentation/vm/hugetlbpage.txt), a Linux kernel feature that enables memory blocks to be managed in larger page sizes.

[note type="positive" status="Interface documentation"]

See [Interface management](/t/interface-management/6154) and [Supported interfaces](/t/supported-interfaces/7744) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>

**Auto-connect**: no

This interface assumes that _huge pages_ are mounted at either:
- `/dev/hugepages` (Debian, Ubuntu)
- `/run/hugepages` (various other distributions)

### Code examples

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/hugepages_control_test.go

The source code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/hugepages_control.go