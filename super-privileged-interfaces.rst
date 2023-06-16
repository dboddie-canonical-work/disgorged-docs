.. 34740.md

.. _super-privileged-interfaces:

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

The following interfaces are considered super-privileged: \| \| \| \|-|-\| \| :ref:`block-devices <the-block-devices-interface>` \| :ref:`classic-support <the-classic-support-interface>` \| \| :ref:`custom-device <the-custom-device-interface>`\ \| :ref:`desktop-launch <the-desktop-launch-interface>` \| \| :ref:`dm-crypt <the-dm-crypt-interface>` \| :ref:`docker <the-docker-interface>` \| \| :ref:`docker-support <the-docker-support-interface>` \|\ :ref:`gpio-control <the-gpio-control-interface>` \| \| :ref:`greengrass-support <the-greengrass-support-interface>` \| :ref:`ion-memory-control <the-ion-memory-control-interface>` \| \| :ref:`kernel-module-control <the-kernel-module-control-interface>` \| :ref:`kernel-module-load <the-kernel-module-load-interface>` \| \| :ref:`kubernetes-support <the-kubernetes-support-interface>` \| :ref:`lxd <the-lxd-interface>` \| \| :ref:`lxd-support <the-lxd-support-interface>` \| :ref:`microstack-support <the-microstack-support-interface>` \| \| :ref:`mount-control <the-mount-control-interface>` \| :ref:`multipass-support <the-multipass-support-interface>` \| \| :ref:`packagekit-control <the-packagekit-control-interface>` \| :ref:`personal-files <the-personal-files-interface>` \| \| :ref:`posix-mq-interface <the-posix-mq-interface>` \| :ref:`sd-control <the-sd-control-interface>` \| \| :ref:`shared-memory <the-shared-memory-interface>` \| :ref:`snapd-control <the-snapd-control-interface>` \| \| :ref:`snap-refresh-control <the-snap-refresh-control-interface>` \| :ref:`snap-themes-control <the-snap-themes-control-interface>` \| \| :ref:`steam-support <the-steam-support-interface>` \| :ref:`system-files <the-system-files-interface>` \| \| :ref:`tee <the-tee-interface>` \| :ref:`uinput <the-uinput-interface>` \| \| :ref:`unity8 <the-unity8-interface>` \|
