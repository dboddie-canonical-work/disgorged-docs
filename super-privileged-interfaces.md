.. 34740.md

.. _super-privileged-interfaces:

# Super-privileged interfaces

Interfaces allow (or deny) access to a resource outside of a snap’s confinement. Generally, any snap can declare any [interface plug](/t/interface-management/6154#heading--slots-plugs).

However, there is a limited set of interfaces that require extra scrutiny when their _plugs_ are included in a snap. This is due to their permissive nature and the control and impact they potentially have over a system.

These interfaces are called **super-privileged**, and snaps that include plugs for super-privileged interfaces require specific [approval from the Store](https://forum.snapcraft.io/t/process-for-aliases-auto-connections-and-tracks/455) before they can be distributed and installed.

<!-- RAW DATA FOR AUTO TABLE FORMATTING
[block-devices](/t/the-block-devices-interface/9721)
[classic-support](/t/the-classic-support-interface/7777)
[desktop-launch](/t/the-desktop-launch-interface/25495)
[dm-crypt](/t/the-dm-crypt-interface/26487)
[docker](/t/the-docker-interface/7787)
[docker-support](/t/the-docker-support-interface/7810)
[gpio-control](/t/the-gpio-control-interface/13037)
[greengrass-support](/t/the-greengrass-support-interface/7831)
[ion-memory-control](/t/the-ion-memory-control-interface/26502)
[kernel-module-control](/t/the-kernel-module-control-interface/7853)
[kubernetes-support](/t/the-kubernetes-support-interface/7855)
[lxd](/t/the-lxd-interface/7863)
[lxd-support](/t/the-lxd-support-interface/7864)
[microstack-support](/t/the-microstack-support-interface/26505)
[multipass-support](/t/the-multipass-support-interface/13095)
[packagekit-control](/t/the-packagekit-control-interface/13052)
[personal-files](/t/the-personal-files-interface/9357)
[sd-control](/t/the-sd-control-interface/25489)
[snapd-control](/t/the-snapd-control-interface/7915)
[snap-refresh-control](/t/the-snap-refresh-control-interface/26569)
[snap-themes-control]()
[steam-support](https://forum.snapcraft.io/t/the-steam-support-interface/30990)
[system-files](/t/the-system-files-interface/9358)
[tee](/t/the-tee-interface/26573)
[uinput](/t/the-uinput-interface/20116)
[unity8](/t/the-unity8-interface/7932)
-->

The following interfaces are considered super-privileged:
| | |
|-|-|
| [block-devices](/t/the-block-devices-interface/9721) | [classic-support](/t/the-classic-support-interface/7777) |
| [custom-device](/t/the-custom-device-interface/29487)| [desktop-launch](/t/the-desktop-launch-interface/25495)  |
| [dm-crypt](/t/the-dm-crypt-interface/26487) | [docker](/t/the-docker-interface/7787) |
| [docker-support](/t/the-docker-support-interface/7810) |[gpio-control](/t/the-gpio-control-interface/13037) |
| [greengrass-support](/t/the-greengrass-support-interface/7831) | [ion-memory-control](/t/the-ion-memory-control-interface/26502) |
| [kernel-module-control](/t/the-kernel-module-control-interface/7853) | [kernel-module-load](/t/the-kernel-module-load-interface/28298) |
| [kubernetes-support](/t/the-kubernetes-support-interface/7855) | [lxd](/t/the-lxd-interface/7863) |
| [lxd-support](/t/the-lxd-support-interface/7864) | [microstack-support](/t/the-microstack-support-interface/26505) |
| [mount-control](/t/the-mount-control-interface/28953) | [multipass-support](/t/the-multipass-support-interface/13095) |
| [packagekit-control](/t/the-packagekit-control-interface/13052) | [personal-files](/t/the-personal-files-interface/9357) |
| [posix-mq-interface](/t/the-posix-mq-interface/31668) | [sd-control](/t/the-sd-control-interface/25489) |
| [shared-memory](/t/the-shared-memory-interface/28382) | [snapd-control](/t/the-snapd-control-interface/7915) |
| [snap-refresh-control](/t/the-snap-refresh-control-interface/26569) | [snap-themes-control](/t/the-snap-themes-control-interface/26827) |
| [steam-support](/t/the-steam-support-interface/30990) | [system-files](/t/the-system-files-interface/9358) |
| [tee](/t/the-tee-interface/26573) | [uinput](/t/the-uinput-interface/20116) |
| [unity8](/t/the-unity8-interface/7932) |