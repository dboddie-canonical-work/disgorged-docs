.. 26487.md

.. _the-dm-crypt-interface:

The dm-crypt interface
======================

The ``dm-crypt`` interface enables the following access functions to `dm-crypt <https://www.kernel.org/doc/html/latest/admin-guide/device-mapper/dm-crypt.html>`__ encrypted external block storage devices:

-  setting up a LUKS partition
-  locking and unlocking *dm-crypt* partitions
-  adding key(s) to kernel keyring
-  formatting encrypted partition(s) ( creation of fs)
-  mounting of encrypted partition(s)

[note type=“positive” status=“Interface documentation”]

See :ref:`Interface management <interface-management>` and :ref:`Supported interfaces <supported-interfaces>` for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-dm-crypt-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

`Auto-connect <interface-management.md#the-dm-crypt-interface-heading--auto-connections>`__: no :ref:`Super-privileged <super-privileged-interfaces>`: yes

Often, *dm-crypt* is statically linked into the kernel (``CONFIG_DM_CRYPT=y``). This is expected when working with custom kernels on projects where disk encryption is required.

Code examples
-------------

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/dm_crypt_test.go

The source code for the interface is in the snapd repository:https://github.com/snapcore/snapd/blob/master/interfaces/builtin/dm_crypt.go
