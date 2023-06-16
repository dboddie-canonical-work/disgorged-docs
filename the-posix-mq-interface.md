.. 31668.md

.. _the-posix-mq-interface:

# The posix-mq interface

The `posix-mq` interface enables inter-process communication (IPC) messages to be created, sent and received between snaps that need to use [POSIX message queues](https://man7.org/linux/man-pages/man7/mq_overview.7.html).

[note type="positive" status="Interface documentation"]

See [Interface management](/t/interface-management/6154) and [Supported interfaces](/t/supported-interfaces/7744) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>

| Permissions |  |  |
|--|--|--|
| **[Auto-connect](/t/interface-management/6154#heading--auto-connections)** | **no** by default | **yes** with snaps from the same publisher |
| **[Super-privileged](/t/super-privileged-interfaces/34740)** | **no** for plugs | **yes** for slots |

**Attributes**:

 * **`posix-mq`** (slot and plug)</br>
   An optional identifier for a message queue. Helps to identify which plugs should connect to which slots. A consumer snap must use the same identifier as the provider snap in order to access the message queue. It defaults to the slot or plug name respectively if not specified.

* **`path`** (slot)</br>
 Messages are shared across one or more paths, depending on the requirements of the snapped applications. The path attribute can either be a string, or an array of strings.

  Each path must adhere to the POSIX message queue naming scheme, outlined on the `mq_overview` [man page](https://man7.org/linux/man-pages/man7/mq_overview.7.html):
   - Each message queue is identified by a name of the form `/somename`; that is, a string of up 255 characters consisting of an initial slash, followed by one or more characters, none of which are slashes.

  An array of paths should be used when the listed queues are meant to be used together, as
  corresponding plugs will get access to all of them.

* **`permissions`** (slot)</br>
  Defines how the messages on the queue can be accessed. Can be either `read`, `write`, `create` or `delete`. Defaults to `read` and `write`.  Permissions are defined on the slot side but apply to the consumer plugs, while the slot side has always all the permissions.

  Any permission allows usage of the `mq_open` and `mq_getsetattr` syscalls, while `read` allows `mq_timedreceive` and `mq_notify`, `write` allows `mq_timedsend`, and `delete` allows `mq_unlink`.

### Code examples

The following definition will create a _posix-mq_ interface with read, write and delete permissions:

```yaml
  test-rwd:
    interface: posix-mq
    path: /test-read-write-delete
    permissions:
      - read
      - write
      - delete
```

The following definition will create a _posix-mq_ interface with read-only permissions for multiple paths:

```yaml
  test-ro-list:
    interface: posix-mq
    path:
      - /test-ro-1
      - /test-ro-2
      - /test-ro-3
      - /test-ro-4
    permissions:
      - read
```

The test code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/posix_mq_test.go

The source code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/posix_mq.go