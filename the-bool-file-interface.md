.. 7803.md

.. _the-bool-file-interface:

# The bool-file interface

The `bool-file` interface allows access to a specific class of file that contains boolean semantics, typically used to toggle or represent the state of binary hardware values.

This interface is primarily intended to be used with [Ubuntu Core](/t/glossary/14612#heading--ubuntu-core) devices, it's also restricted because it provides privileged access to hardware.

These kinds of file are located within specific directories inside the [sysfs](https://man7.org/linux/man-pages/man5/sysfs.5.html) filesystem (`/sys`) and this  interface allows a file to be _read_, to obtaining a current value, or _written to_, setting a new value.

The [LED class](https://www.kernel.org/doc/html/latest/leds/leds-class.html) is a good example of file type for this interface, as it potentially allows LEDs to be turned on and off, and have their brightness modified.

Use the  `snap interface bool-file` command to see which boolean files are available on the system:

```bash
$ snap interface bool-file
name:    bool-file
summary: allows access to specific file with bool semantics
slots:
  - my-gadget:green-led
  - my-gadget:red-led
[...]
```

[note type="positive" status="Interface documentation"]

See [Interface management](/t/interface-management/6154) and [Supported interfaces](/t/supported-interfaces/7744) for further details on how interfaces are used.
[/note]

---

<h2 id='heading--dev-details'>Developer details </h2>


**[Auto-connect](/t/interface-management/6154#heading--auto-connections)**: no</br>

**Attributes**:
 * `path` (slot): path to the file in _sysfs_</br>
     Example: `/sys/class/leds/green/brightness`</br>

   The path value must match one of the following regular expressions:</br>
   - For GPIO devices:
 `^/sys/class/gpio/gpio[0-9]+/value$`</br>
   - For LED devices: `^/sys/class/leds/[^/]+/brightness$`

The [gpio interface](/t/the-gpio-interface/7829)  provides another option for accessing GPIO devices.

To use a boolean file, the snap developer must add `plugs: [ bool-file ]` to a snap's [snapcraft.yaml](/t/the-snapcraft-format/8337). The snap user can then access a specific boolean file with an [interface connection](/t/interface-management/6154#heading--manual-connections).

Unless a snap specifically expects a set of boolean files that cannot be predefined, the recommended approach is to define distinct plugs for each boolean file the snap wishes to use:

```yaml
plugs:
  green-led:
    interface: bool-file
  red-led:
    interface: bool-file
```

Defining distinct plugs for each boolean file has the advantage of being self-documenting, and 1:1  connections like these are easier to track and setup with [auto-connections](/t/the-interface-auto-connection-mechanism/20179), if needed.

Once connected, the consuming snap can use the boolean file via the path mentioned in the `path` attribute specified by the connected slot.

The slot side on a gadget snap may be declared as follows:

```yaml
slots:
  green-led:
    interface: bool-file
    path: /sys/class/leds/green0/brightness
  red-led:
    interface: bool-file
    path: /sys/class/leds/red0/brightness
```

### Code examples

The test code for this interface can be found in the snapd repository:</br>
[https://github.com/snapcore/snapd/blob/master/interfaces/builtin/bool_file_test.go](https://github.com/snapcore/snapd/blob/master/interfaces/builtin/bool_file_test.go)

The source code for the interface is in the snapd repository:</br>
[https://github.com/snapcore/snapd/blob/master/interfaces/builtin/bool_file.go](https://github.com/snapcore/snapd/blob/master/interfaces/builtin/bool_file.go)

> ⓘ  This is a snap interface. See [Interface management](/t/interface-management/6154) and [Supported interfaces](/t/supported-interfaces/7744) for further details on how interfaces are used.