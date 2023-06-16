.. 7829.md

.. _the-gpio-interface:

The gpio interface
==================

``gpio`` allows access to a specific GPIO pin. The interface is restricted because it provides privileged access to GPIO hardware.

Use ``snap interface gpio`` to see which gpio devices are available on the system:

.. code:: bash

   $ snap interface gpio
   name:    gpio
   summary: allows access to specifc GPIO pin
   slots:
     - pi:bcm-gpio-0
     - pi:bcm-gpio-1
     - pi:bcm-gpio-10
   [...]

.. raw:: html

   <h2 id="the-gpio-interface-heading--example">

Example

.. raw:: html

   </h2>

The `pi-fancontrol <https://snapcraft.io/pi-fancontrol>`__ snap provides simple fan control on a Raspberry Pi with a fan connected to GPIO 14 (pin 8). With the snap installed, the following command will connect the interface to the pin:

.. code:: bash

   snap connect pi-fancontrol:gpio pi:bcm-gpio-14

.. note::


          See :ref:`Interface management <interface-management>` and :ref:`Supported interfaces <supported-interfaces>` for further details on how interfaces are used.

--------------

.. raw:: html

   <h2 id="the-gpio-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

**Auto-connect**: no **Attributes**: \* ``number`` (slot): GPIO pin number to export and expose to consuming snaps

:ref:`Hardware IO interfaces <hardware-io-interfaces>` covers some general considerations common to these kinds of devices.

To use a gpio device, the snap developer must add :ref:``plugs: [ gpio ]`` to a snap’s `snapcraft.yaml <the-snapcraft-yaml-schema>`. The snap user can then access a specific gpio device with an `interface connection <interface-management.md#the-gpio-interface-heading--manual-connections>`__.

Unless the snap is expected to actually use a set of gpio pins that is not predefined, it is recommended to define distinct plugs for each used gpio pin, like:

.. code:: yaml

   plugs:
     activity-led:
       interface: gpio
     warning-led:
       interface: gpio

This has the advantage of being self-documenting and 1-1 connections like these are easier to track and setup with :ref:`auto-connections <the-interface-auto-connection-mechanism>`, if the latter is needed.

When the interface is connected, ``"echo (pin number) > /sys/class/gpio/export"`` is run internally to enable access to the GPIO pin.

Once connected, the consuming snap can use the device via ``/sys/class/gpio/gpioN`` where ``N`` is the pin number specified by the connected slot.

Finally, when the interface is disconnected, ``"echo (pin number) > /sys/class/gpio/unexport"`` is run internally to disable access to the GPIO pin.

.. raw:: html

   <h3 id="the-gpio-interface-heading-code">

Code examples

.. raw:: html

   </h3>

The hook and control scripts for *pi-fancontrol* can be found in the project’s GitHub repository: https://github.com/ogra1/pi-fancontrol-snap

The source code for the GPIO interface is in the *snapd* repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/gpio.go.
