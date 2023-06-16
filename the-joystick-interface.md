.. 7849.md

.. _the-joystick-interface:

# The joystick interface

`joystick` allows access to joystick devices.

The interface can access `/dev/input/js*` (with snap version _2.24+_) and `/dev/input/event*` (with snap version _2.33+_) devices that are udev marked with `ID_INPUT_JOYSTICK=1`.

**Auto-connect**: no

Requires snapd version _2.24+_.

> ⓘ  This is a snap interface. See [Interface management](/t/interface-management/6154) and [Supported interfaces](/t/supported-interfaces/7744) for further details on how interfaces are used.