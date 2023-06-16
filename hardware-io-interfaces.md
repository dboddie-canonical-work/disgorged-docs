.. 35421.md

.. _hardware-io-interfaces:

# Hardware IO interfaces

Hardware IO (input/output) interfaces, including the [serial-port](the-serial-port-interface.md), [gpio](the-gpio-interface.md) and [i2c](the-i2c-interface.md) interfaces, are designed to be used on devices running [Ubuntu Core](glossary.md#hardware-io-interfaces-heading--ubuntu-core). These interfaces are driven from a device's [gadget snap](gadget-snaps.md) which is used to define and configure a device's system properties.

This approach is more robust because it allows the gadget snap providing the slot to centralise and arbitrate the connection conditions. These conditions include which other snaps, identified by  their snap ID, can connect to the slots the gadget offers and, consequently, gain privileged access to the hardware.  For the application snap, usually no change is required other than to declare and use an appropriately-configured plug.

- [Interface considerations](#hardware-io-interfaces-heading--considerations)
- [Code examples](#hardware-io-interfaces-heading--examples)

<h2 id='hardware-io-interfaces-heading--considerations'>Interface considerations</h2>

The extent of access an interface has is granted through both _connection permissions_ and the specifics of the _interface connections_ being requested.

1. **Connection permissions**: [auto-connect](the-interface-auto-connection-mechanism.md) | [privileged](interface-management.md) | [super-privileged](super-privileged-interfaces.md)
   </br>Connection requirements are dependent on which store a developer is using.
     - [Global Snap Store](glossary.md#hardware-io-interfaces-heading--snap-store): privileged and super-privileged interfaces require store approval because of the level of trust and permissiveness these interfaces have, which is also why certain interfaces need certain oversight. See [Permission requests](permission-requests.md) for further details.
    * [Dedicated Snap Store](glossary.md#hardware-io-interfaces-heading--dedicated): trust and permissiveness are now  the responsibility of the store owner, and many privileged interface connections can be self-served and defined within the dedicated snap store and the device context.
1. **Interface connections**: hardware IO interfaces | app-provided interfaces | other interfaces
    * **Hardware IO interfaces**: These require either a [slot](interface-management.md#hardware-io-interfaces-heading--slots-plugs) to be defined by a device's _gadget snap_ or an interface with [Hotplug support](https://snapcraft.io/docs/hotplug-support), in which case the slot appears from the system snap.
      * An unconstrained [auto-connection](the-interface-auto-connection-mechanism.md#hardware-io-interfaces-heading--autoconnect) cannot be used because there may be _many slots of a given interface_, resulting in ambiguity that requires  an extensive set of store rules to manage and maintain.
      * Each plug should therefore be connected to a slot, for example:
        * green led plug on app => green led slot on gadget
        * red led plug on app => red led slot on gadget
      - This kind of 1-to-1 connections can usually be established via [slot rules in the snap-declaration](the-interface-auto-connection-mechanism.md) for the gadget.
    * **App-provided interfaces**: slots are defined by apps, or occasionally from the gadget snap,
      * May require access, such as from the [content](the-content-interface.md) or [shared-memory](the-shared-memory-interface.md) interfaces.
      * A slot might may be provided by the system snap to cover the case of an equivalent system service, such as [audio-playback](the-audio-playback-interface.md)
      * the slot might be [super-privileged](super-privileged-interfaces.md)
    * **Other interfaces**: For more system level access, slots are provided by the system snap.

<h3 id='hardware-io-interfaces-heading--code-examples'>Code examples</h3>

The [gadget snap](https://github.com/snapcore/pi-gadget/tree/20-arm64) definition for the reference [Raspberry Pi Ubuntu Core](https://ubuntu.com/core/docs/install-raspberry-pi) image contains interface definitions for various hardware IO interfaces on the system, including slots for each specific GPIO pin, i2c connections, the Bluetooth serial port, and the generic serial ports:

```yaml
slots:
  bcm-gpio-0:
    interface: gpio
    number: 0
  bcm-gpio-1:
    interface: gpio
    number: 1
  bcm-gpio-2:
    interface: gpio
    number: 2
[...]
  i2c-0:
    interface: i2c
    path: /dev/i2c-0
[...]
  bt-serial:
    interface: serial-port
    path: /dev/ttyAMA0
[...]
  serial0:
    interface: serial-port
    path: /dev/ttyS0
  serial1:
    interface: serial-port
    path: /dev/ttyS1
```

On a Raspberry Pi, the above hardware IO interfaces are accessible to apps from the system snap without requiring any further configuration.