.. 7915.md

.. _the-snapd-control-interface:

# The snapd-control interface

The `snapd-control` interface enables snap management, such as snap installation, removal and refresh-control by communicating with the snapd daemon.

Due to its ability to permit the installation any snap at potentially any confinement level, `snapd-control` is primarily intended to be used by [brand store](https://core.docs.ubuntu.com/en/build-store/#brand-stores) owners as they will typically already have full access to their devices.

Consequently, consumers of this interface require [approval](/t/process-for-aliases-auto-connections-and-tracks/455/) for distribution via the Snap Store, and this approval is only likely to be given under strict and specific circumstances.

[note type="positive" status="Interface documentation"]

See [Interface management](/t/interface-management/6154) and [Supported interfaces](/t/supported-interfaces/7744) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>


**[Auto-connect](/t/interface-management/6154#heading--auto-connections)**: no</br>
**[Super-privileged](/t/super-privileged-interfaces/34740)**: yes</br>

**Attributes** :
 * `refresh-schedule` (plug):  can be set to `managed` to signal an intention to permit only manual refreshes for the snap:

   ```yaml
   plugs:
       snapd:
           interface: snapd-control
           refresh-schedule: managed
    ```

   Permitting only manual refreshes is a 3 stage process with the above being the first stage. The second stage is to connect the interface, effectively granting permission for refresh management while the third is to set the following _core_ system setting:

   ```bash
   sudo snap set core refresh.timer=managed
   ```
   The last step activates the manual-only refresh option, skipping upcoming refresh attempts. These values are rechecked and reconfirmed before every future refresh attempt. If any of the steps stop being true, the snap refresh proceeds.

### Code examples

The source code can be found in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/snapd_control.go

The test code for the interface is in the snapd repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/snapd_control_test.go