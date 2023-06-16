.. 26487.md

.. _the-dm-crypt-interface:

# The dm-crypt interface

The `dm-crypt`  interface enables the following access functions to  [dm-crypt](https://www.kernel.org/doc/html/latest/admin-guide/device-mapper/dm-crypt.html) encrypted external block storage devices:

- setting up a LUKS partition
- locking and unlocking _dm-crypt_ partitions
- adding key(s) to kernel keyring
- formatting encrypted partition(s) ( creation of fs)
- mounting of encrypted partition(s)

[note type="positive" status="Interface documentation"]

See [Interface management](interface-management.md) and [Supported interfaces](supported-interfaces.md) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>

**[Auto-connect](interface-management.md#heading--auto-connections)**: no
**[Super-privileged](super-privileged-interfaces.md)**: yes

Often, _dm-crypt_ is statically linked into the kernel (`CONFIG_DM_CRYPT=y`). This is expected when working with custom kernels on projects where disk encryption is required.

### Code examples

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/dm_crypt_test.go

The source code for the interface is in the snapd repository:[ https://github.com/snapcore/snapd/blob/master/interfaces/builtin/dm_crypt.go](https://github.com/snapcore/snapd/blob/master/interfaces/builtin/dm_crypt.go)