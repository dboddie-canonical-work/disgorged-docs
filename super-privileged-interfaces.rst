.. 34740.md

.. \_super-privileged-interfaces:

Super-privileged interfaces
===========================

Interfaces allow (or deny) access to a resource outside of a snap’s confinement. Generally, any snap can declare any `interface plug <interface-management.md#super-privileged-interfaces-heading--slots-plugs>`__.

However, there is a limited set of interfaces that require extra scrutiny when their *plugs* are included in a snap. This is due to their permissive nature and the control and impact they potentially have over a system.

These interfaces are called **super-privileged**, and snaps that include plugs for super-privileged interfaces require specific `approval from the Store <https://snapcraft.io/docs/process-for-aliases-auto-connections-and-tracks>`__ before they can be distributed and installed.

.. raw:: html

   <!-- RAW DATA FOR AUTO TABLE FORMATTING
   [block-devices](the-block-devices-interface.md)
   [classic-support](the-classic-support-interface.md)
   [desktop-launch](the-desktop-launch-interface.md)
   [dm-crypt](the-dm-crypt-interface.md)
   [docker](the-docker-interface.md)
   [docker-support](the-docker-support-interface.md)
   [gpio-control](the-gpio-control-interface.md)
   [greengrass-support](the-greengrass-support-interface.md)
   [ion-memory-control](the-ion-memory-control-interface.md)
   [kernel-module-control](the-kernel-module-control-interface.md)
   [kubernetes-support](the-kubernetes-support-interface.md)
   [lxd](the-lxd-interface.md)
   [lxd-support](the-lxd-support-interface.md)
   [microstack-support](the-microstack-support-interface.md)
   [multipass-support](the-multipass-support-interface.md)
   [packagekit-control](the-packagekit-control-interface.md)
   [personal-files](the-personal-files-interface.md)
   [sd-control](the-sd-control-interface.md)
   [snapd-control](the-snapd-control-interface.md)
   [snap-refresh-control](the-snap-refresh-control-interface.md)
   [snap-themes-control]()
   [steam-support](the-steam-support-interface.md)
   [system-files](the-system-files-interface.md)
   [tee](the-tee-interface.md)
   [uinput](the-uinput-interface.md)
   [unity8](the-unity8-interface.md)
   -->

The following interfaces are considered super-privileged: \| \| \| \|-|-\| \| `block-devices <the-block-devices-interface.md>`__ \| `classic-support <the-classic-support-interface.md>`__ \| \| `custom-device <the-custom-device-interface.md>`__\ \| `desktop-launch <the-desktop-launch-interface.md>`__ \| \| `dm-crypt <the-dm-crypt-interface.md>`__ \| `docker <the-docker-interface.md>`__ \| \| `docker-support <the-docker-support-interface.md>`__ \|\ `gpio-control <the-gpio-control-interface.md>`__ \| \| `greengrass-support <the-greengrass-support-interface.md>`__ \| `ion-memory-control <the-ion-memory-control-interface.md>`__ \| \| `kernel-module-control <the-kernel-module-control-interface.md>`__ \| `kernel-module-load <the-kernel-module-load-interface.md>`__ \| \| `kubernetes-support <the-kubernetes-support-interface.md>`__ \| `lxd <the-lxd-interface.md>`__ \| \| `lxd-support <the-lxd-support-interface.md>`__ \| `microstack-support <the-microstack-support-interface.md>`__ \| \| `mount-control <the-mount-control-interface.md>`__ \| `multipass-support <the-multipass-support-interface.md>`__ \| \| `packagekit-control <the-packagekit-control-interface.md>`__ \| `personal-files <the-personal-files-interface.md>`__ \| \| `posix-mq-interface <the-posix-mq-interface.md>`__ \| `sd-control <the-sd-control-interface.md>`__ \| \| `shared-memory <the-shared-memory-interface.md>`__ \| `snapd-control <the-snapd-control-interface.md>`__ \| \| `snap-refresh-control <the-snap-refresh-control-interface.md>`__ \| `snap-themes-control <the-snap-themes-control-interface.md>`__ \| \| `steam-support <the-steam-support-interface.md>`__ \| `system-files <the-system-files-interface.md>`__ \| \| `tee <the-tee-interface.md>`__ \| `uinput <the-uinput-interface.md>`__ \| \| `unity8 <the-unity8-interface.md>`__ \|
