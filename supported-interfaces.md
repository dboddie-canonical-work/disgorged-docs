.. 7744.md

.. _supported-interfaces:

# Supported interfaces

Interfaces enable resources from one snap to be shared with another and with the system. For a snap to use an interface, its developer needs to have first defined its corresponding plugs and slots within a snap's [snapcraft.yaml](creating-snapcraft-yaml.md) file.

> ℹ For details on how to add an interface to your own snap, see [Snapcraft interfaces](adding-interfaces.md). For general usage details, see [Interface management](interface-management.md).

The table below lists currently supported interfaces, with links to further details for each interface.

The following column names are used:

- **Interface** is the syntactical interface name, as used by snaps.

- **Description** is a brief overview of what the interface permits. Select the interface name to open the interface-specific page for a more detailed description on each interface.

- **Categories** are used to split interfaces into broad types, and also to indicate what kind of access they permit. Video, graphics and audio are typical desktop requirements, for example, while VM, Container, Kernel and Developer imply more specific roles. The Ubuntu Core category is used to denote when an interface is intended for [Ubuntu Core](glossary.md#supported-interfaces-heading--ubuntu-core), and _Super privileged_ is used when an interface requires extra security scrutiny. See [Super-privileged interfaces](super-privileged-interfaces.md) for more information.

- **Auto-connect** indicates that the interface will be connected by default when the snap is first installed, requiring no further user action. If `Auto-connect=no`, an interface can still be automatically connected if the snap developer has requested, and been granted, explicit permission. See [Interface connection mechanism](the-interface-auto-connection-mechanism.md) for details.

 **Important:** if a snap is installed prior to an interface being granted auto-connect permission, and permission is subsequently granted and the snap updated, when the installed snap updates, the interface will be auto-connected.

| Interface | Description | Categories | Auto-connect |
|---|----|---|---|
| [account-control](the-account-control-interface.md) | add/remove user accounts or change passwords | System, Account | no |
| [accounts-service](the-accounts-service-interface.md) | allows communication with the accounts service | System, Account | no |
| [acrn](the-acrn-interface.md) | allows access to user VMs using the ACRN hypervisor | VM, Hypervisor, Developer | no |
| [adb-support](the-adb-support-interface.md) | allows operating as Android Debug Bridge service | ADB, Developer | no |
| [allegro-vcu](the-allegro-vcu-interface.md) | access the Allegro Video Core Unit | Video, Graphics | no |
| [alsa](the-alsa-interface.md) | play or record sound | Audio | no |
| [appstream-metadata](the-appstream-metadata-interface.md) | allows access to AppStream metadata | System, Developer, Manage software | no |
| [audio-playback](the-audio-playback-interface.md) | allows audio playback via supporting services | Audio, Playback | yes |
| [audio-record](the-audio-record-interface.md) | allows audio recording via supported services | Audio, Record | no |
| [autopilot-introspection](the-autopilot-introspection-interface.md) | be controlled by Autopilot software | System, Developer | no |
| [avahi-control](the-avahi-control-interface.md) | advertise services over the local network | Network, Local network, Nearby devices | no |
| [avahi-observe](the-avahi-observe-interface.md) | detect services and devices over the local network | Network, Local network, Nearby devices | no |
| [block-devices](the-block-devices-interface.md) | access to disk block devices | Super privileged, Storage, Low level | no |
| [bluetooth-control](the-bluetooth-control-interface.md) | access Bluetooth hardware directly | Network, Bluetooth, Nearby devices | no |
| [bluez](the-bluez-interface.md) | use Bluetooth devices | Network, Bluetooth, Nearby devices | no |
| [bool-file](the-bool-file-interface.md) | allows access to specific file with bool semantics | System, Low level, Privileged | no |
| [broadcom-asic-control](the-broadcom-asic-control-interface.md) | control Broadcom network switches | Network, System | no |
| [browser-support](the-browser-support-interface.md) | use functions essential for Web browsers | Browser, Network | no when allow-sandbox: true, yes otherwise |
| [calendar-services](the-calendar-service-interface.md) | allows communication with Evolution Data Server calendar | Personal data, Contacts and calendar | no |
| [camera](the-camera-interface.md) | use your camera or webcam | Camera, Personal data | no |
| [can-bus](the-can-bus-interface.md) | allows access to the CAN bus | System, Developer | no |
| [cifs-mount](the-cifs-mount-interface.md) | allows the mounting and unmounting of CIFS filesystems | Storage | no |
| [classic-support](the-classic-support-interface.md) | enable resource access to classic snap | Super privileged, Ubuntu Core | no |
| [contacts-service](the-contacts-service-interface.md) | allows communication with the Evolution Data Server address book | Personal data, Contacts and calendar | no |
| [content](the-content-interface.md) | access resources across snaps | Storage, Files, Attributes | yes for snaps from same publisher, no otherwise |
| [core-support](the-core-support-interface.md) | deprecated since snap 2.34 | System, Other | no |
| [cpu-control](the-cpu-control-interface.md) | set certain CPU values | System, Developer | no |
| [cups](the-cups-interface.md) | access to the CUPS socket for printing | Printing | not applicable |
| [cups-control](the-cups-control-interface.md) | print documents | Printing | no |
| [custom-device](the-custom-device-interface.md) | permits access to a specific class of device | Super privileged, Ubuntu Core | no |
| [daemon-notify](the-daemon-notify-interface.md) | allows sending daemon status changes to service manager | System, Developer | no |
| [dbus](the-dbus-interface.md) | allow snaps to communicate over D-Bus | System, Developer | no |
| [dcdbas-control](the-dcdbas-control-interface.md) | shut down or restart Dell devices | Developer | no |
| [desktop](the-desktop-interface.md) | provides access to common desktop elements | Desktop | yes |
| [desktop-launch](the-desktop-launch-interface.md) | identify and launch desktop apps from other snaps | Super privileged, Desktop | no |
| [desktop-legacy](the-desktop-legacy-interface.md) | enables the use of legacy desktop methods (including input method and accessibility services) | Desktop | yes |
| [device-buttons](the-device-buttons-interface.md) | use any device-buttons | Hardware, Developer | no |
| [display-control](the-display-control-interface.md) | allows configuring display parameters | Display, Graphics | no |
| [dm-crypt](the-dm-crypt-interface.md) | access encrypted storage devices | Super privileged, Ubuntu Core, Storage | no |
| [docker](the-docker-interface.md) | start, stop, or manage Docker containers | Super privileged, Containers | no |
| [docker-support](the-docker-support-interface.md) | allows operating as the Docker daemon | Super privileged, Containers | no |
| [dsp](the-dsp-interface.md) | enables the control of digital signal processors (DSPs) | Hardware, Developer | no |
| [dummy](the-empty-interface.md) | renamed to empty interface | System, Other | no |
| [dvb](the-dvb-interface.md) | allows access to all DVB devices and APIs | Hardware, Developer | no |
| [empty](the-empty-interface.md) | allows testing without additional permissions | System, Other | no |
| [firewall-control](the-firewall-control-interface.md) | configure a network firewall | Networking | no |
| [fpga](the-fpga-interface.md) | permits access to an FPGA subsystem | Hardware, Developer | no |
| [framebuffer](the-framebuffer-interface.md) | access to universal framebuffer devices | Hardware, Developer | no |
| [fuse-support](the-fuse-support-interface.md) | enables access to the FUSE filesystems | Storage | no |
| [fwupd](the-fwupd-interface.md) | allows operating as the fwupd service | System, Security, Firmware | no |
| [gconf](the-gconf-interface.md) | access the legacy GConf config system | System, Developer, Settings | no |
| [gpg-keys](the-gpg-keys-interface.md) | read GPG user configuration and keys | GPG, Personal data, Security | no |
| [gpg-public-keys](the-gpg-public-keys-interface.md) | read GPG non-sensitive configuration and public keys | GPG, Personal data, Security | no |
| [gpio](the-gpio-interface.md) | access specific GPIO pins | GPIO, Hardware, Developer | no |
| [gpio-control](the-gpio-control-interface.md) | allows to export/unexport and control all GPIOs | Super privileged, GPIO | no |
| [gpio-memory-control](the-gpio-memory-control-interface.md) | allows write access to all GPIO memory | GPIO, Hardware, Developer | no |
| [greengrass-support](the-greengrass-support-interface.md) | allows operating as the Greengrass service | Super privileged, Edge, AWS, Discrete | no |
| [gsettings](the-gsettings-interface.md) | provides access to any GSettings item for current user | System, Developer, Settings | yes |
| [hardware-observe](the-hardware-observe-interface.md) | access hardware information | System, Hardware | no |
| [hardware-random-control](the-hardware-random-control-interface.md) | provide entropy to hardware random number generator | System, Hardware | no |
| [hardware-random-observe](the-hardware-random-observe-interface.md) | use hardware-generated random numbers | System, Hardware | no |
| [hidraw](the-hidraw-interface.md) | access hidraw devices | System | no |
| [home](the-home-interface.md) | access non-hidden files in the home directory | Storage, Personal data | yes on classic (traditional distributions), no otherwise |
| [hostname-control](the-hostname-control-interface.md) | allows configuring the system hostname | Networking | no |
| [hugepages-control](the-hugepages-control-interface.md) | control HugePages memory blocks | System, Memory, Kernel | no |
| [i2c](the-i2c-interface.md) | access i²c devices | System, Hardware | no |
| [iio](the-iio-interface.md) | access IIO devices | System, Hardware | no |
| [intel-mei](the-intel-mei-interface.md) | access to the Intel MEI management interface | System, Firmware | no |
| [io-ports-control](the-io-ports-control-interface.md) | allows access to all I/O ports | System, | no |
| [ion-memory-control](the-ion-memory-control-interface.md) | access Android's ION memory allocator | System  | no |
| [jack1](the-jack1-interface.md) | allows interaction with the JACK audio connection server | Audio | no |
| [joystick](the-joystick-interface.md) | use any connected joystick | Hardware, Developer | no |
| [juju-client-observe](the-juju-client-observe-interface.md) | read the Juju client configuration | Developer, Discrete | no |
| [kernel-crypto-api](the-kernel-crypto-api-interface.md) | read and manage kernel supported crypto ciphers | System, Kernel, Security | no |
| [kernel-module-control](the-kernel-module-control-interface.md) | insert, remove and query kernel modules | Super priviliged, System, Kernel | no |
| [kernel-module-load](the-kernel-module-load-interface.md) | load, or deny loading, specific kernel modules | Super priviliged, System, Kernel | no |
| [kernel-module-observe](the-kernel-module-observe-interface.md) | query kernel modules | System, Kernel | no |
| [kubernetes-support](the-kubernetes-support-interface.md) | use functions essential for Kubernetes | Super priviliged, Hypervisor, Discrete | no |
| [kvm](the-kvm-interface.md) | allows access to the kvm device | VM, Hypervisor, Developer | no |
| [libvirt](the-libvirt-interface.md) | provides access to the libvirt service | VM, Hypervisor, Developer | no |
| [locale-control](the-locale-control-interface.md) | change system language and region settings | Language and region, Personalisation | no |
| [location-control](the-location-control-interface.md) | allows operating as the location service | Location | no |
| [location-observe](the-location-observe-interface.md) | access your location | Location | no |
| [log-observe](the-log-observe-interface.md) | read system logs | System, Developer | no |
| [login-session-control](the-login-session-control-interface.md) | allows setup of login sessions and grants privileged access to user sessions | System, Security | no |
| [login-session-observe](the-login-session-observe-interface.md) | allows reading login and session information | System, Security | no |
| [lxd](the-lxd-interface.md) | provides access to the LXD socket | Super privileged, Container, Discrete | no |
| [lxd-support](the-lxd-support-interface.md) | allows operating as the LXD service | Super privileged, Container, Discrete | no |
| [maliit](the-maliit-interface.md) | use an on-screen keyboard | Developer | no |
| [media-control](the-media-control-interface.md) | access media control devices and Video4Linux (V4L) devices | Hardware, Developer, Video | no |
| [media-hub](the-media-hub-interface.md) | access snaps providing the media-hub interface | Developer, Media | yes |
| [microstack-support](the-microstack-support-interface.md) | multiple service access to the Microstack infrastructure | Super privileged, Container, Discrete | no |
| [mir](the-mir-interface.md) | enables access to the Mir display service | Display | yes |
| [modem-manager](the-modem-manager-interface.md) | use and configure modems | Networking | no |
| [mount-control](the-mount-control-interface.md) | mount and unmount transient and persistent filesystem mount points | Super privileged, Storage | no |
| [mount-observe](the-mount-observe-interface.md) | read mount table and quota information | Storage | no |
| [mpris](the-mpris-interface.md) | media key control of music and video players | Sound | no |
| [multipass-support](the-multipass-support-interface.md) | multipass-support allows operating as the Multipass service | Super privileged, VM, Discrete | no |
| [netlink-audit](the-netlink-audit-interface.md) | allows access to kernel audit system through Netlink | Inter-process communication (IPC), Netlink, Developer | no |
| [netlink-connector](the-netlink-connector-interface.md) | communicate through the kernel Netlink connector | Inter-process communication (IPC), Netlink, Developer | no |
| [netlink-driver](the-netlink-driver-interface.md) | operate a kernel driver module exposed via Netlink | Inter-process communication (IPC), Netlink, Developer | no |
| [network](the-network-interface.md) | enables network access | Networking | yes |
| [network-bind](the-network-bind-interface.md) | operate as a network service | Networking | yes |
| [network-control](the-network-control-interface.md) | change low-level network settings | Networking | no |
| [network-manager](the-network-manager-interface.md) | configure and observe networking via NetworkManager | Networking | no |
| [network-manager-observe](the-network-manager-observe-interface.md) | allows observing NetworkManager settings | Networking | no |
| [network-observe](the-network-observe-interface.md) | query network status information | Networking | no |
| [network-setup-control](the-network-setup-control-interface.md) | change network settings via Netplan | Networking | no |
| [network-setup-observe](the-network-setup-observe-interface.md) | read network settings | Networking | no |
| [network-status](the-network-status-interface.md) | access the NetworkingStatus service | Networking | yes |
| [ofono](the-ofono-interface.md) | allows operating as the oFono service | Networking, Discrete, Developer | no |
| [online-accounts-service](the-online-accounts-service-interface.md) | access to the Online Accounts service | Service, Developer | yes |
| [opengl](the-opengl-interface.md) | access OpenGL/GPU hardware | Display, Graphics | yes |
| [openvswitch](the-openvswitch-interface.md) | control Open vSwitch hardware | Networking, Service, Developer | no |
| [openvswitch-support](the-openvswitch-support-interface.md) | enables kernel support for Open vSwitch | Networking, Service, Developer | no |
| [optical-drive](the-optical-drive-interface.md) | read/write access to CD/DVD drives | Storage, Hardware, Developer | yes, unless drive can write |
| [packagekit-control](the-packagekit-control-interface.md) | control the PackageKit service | Super privileged, Packaging | no |
| [password-manager-service](the-password-manager-service-interface.md) | read, add, change, or remove saved passwords | System, Security | no |
| [personal-files](the-personal-files-interface.md) | read or write files in the user's home directory | Super privileged, Personal data, Attributes | no |
| [physical-memory-control](the-physical-memory-control-interface.md) | read and write memory used by any process | System, Memory, Kernel | no |
| [physical-memory-observe](the-physical-memory-observe-interface.md) | read memory used by any process | System, Memory, Kernel | no |
| [polkit](the-polkit-interface.md) | access to the polkit authorisation manager | System, Security | no |
| [posix-mq](the-posix-mq-interface.md) | enables inter-process communication (IPC) messages | Super privileged, IPC | no by default, yes with snaps from the same publisher |
| [power-control](the-power-control-interface.md) | read and write system power settings | System, Power | no |
| [ppp](the-ppp-interface.md) | access to configure and observe PPP networking | Networking | no |
| [process-control](the-process-control-interface.md) | pause or end any process on the system | System | no |
| [ptp](the-ptp-interface.md) | access to the Precision Time Protocol subsystem | System, Developer | no |
| [pulseaudio](the-pulseaudio-interface.md) | play and record sound | Audio | no |
| [pwm](the-pwm-interface.md) | access specific PWM channels | System, Developer, Hardware, WIP | no |
| [qualcomm-ipc-router](the-qualcomm-ipc-router-interface.md) | access Qualcomm IPC router sockets | IPC, Kernel, System | no |
| [raw-input](the-raw-input-interface.md) | access raw input devices directly | System, Developer, Hardware | no |
| [raw-usb](the-raw-usb-interface.md) | access USB hardware directly | System, Developer, Hardware | no |
| [raw-volume](the-raw-volume-interface.md) | access specific disk partitions | Storage | no |
| [removable-media](the-removable-media-interface.md) | read/write files on removable storage devices | Storage | no |
| [screencast-legacy](the-screencast-legacy-interface.md) | allows screen recording and audio recording alongside writing to arbitrary filesystem paths | Legacy | no |
| [screen-inhibit-control](the-screen-inhibit-control-interface.md) | prevent screen sleep, lock and screensaver | Display | yes |
| [scsi-generic](the-scsi-generic-interface.md) | read and write access to SCSI Generic driver devices | Storage | no |
| [sd-control](the-sd-control-interface.md) | control SD cards on specific devices | Super privileged, Storage | no |
| [serial-port](the-serial-port-interface.md) | access serial port hardware | System, Developer, Hardware | no by default, yes with snaps from the same publisher |
| [shared-memory](the-shared-memory-interface.md) | enables two snaps to access the same shared memory | Super privileged, IPC | no |
| [shutdown](the-shutdown-interface.md) | restart or power off the device | System, Power | no |
| [snap-refresh-control](the-snap-refresh-control-interface.md) | permits bespoke snap refresh control | Super privileged, Packaging | no |
| [snapd-control](the-snapd-control-interface.md) | install or remove software | Super privileged, Packaging | no |
| [spi](the-spi-interface.md) | access specific SPI devices | System, Developer, Hardware | no |
| [ssh-keys](the-ssh-keys-interface.md) | access SSH private and public keys | Security | no |
| [ssh-public-keys](the-ssh-public-keys-interface.md) | access SSH public keys | Security | no |
| [steam-support](the-steam-support-interface.md) | allows the Steam snap to access pressure-vessel containers | Super privileged, Discrete | no |
| [storage-framework-service](the-storage-framework-service-interface.md) | operate as, or interact with, the Storage Framework | Storage | no |
| [system-backup](the-system-backup-interface.md) | read-only access to the system for backups | Storage | no |
| [system-files](the-system-files-interface.md) | read or write files in the system | Super privileged, Storage, Attributes | no |
| [system-observe](the-system-observe-interface.md) | read process and system information | Monitoring, System | no |
| [system-packages-doc](the-system-packages-doc-interface.md) | access system documentation in /usr/share/doc | Developer | no |
| [system-source-code](the-system-source-code-interface.md) | access kernel source and headers in /usr/src | Developer | no |
| [system-trace](the-system-trace-interface.md) | monitor or control any running program | Monitoring, System | no |
| [tee](the-tee-interface.md) | permits access to the Trusted Execution Environment | Super privileged, Security, Ubuntu Core | no |
| [thumbnailer-service](the-thumbnailer-service-interface.md) | create thumbnail images from local media files | Storage, Media | no |
| [time-control](the-time-control-interface.md) | change the date and time | Time | no |
| [timeserver-control](the-timeserver-control-interface.md) | change time server settings | Time | no |
| [timezone-control](the-timezone-control-interface.md) | change the time zone | Time | no |
| [tpm](the-tpm-interface.md) | allows access to the Trusted Platform Module device | Kernel, Security | no |
| [u2f-devices](the-u2f-devices-interface.md) | use any U2F devices | Security, Hardware, Developer | no |
| [ubuntu-download-manager](the-ubuntu-download-manager-interface.md) | use the Ubuntu Download Manager | System, Developer, Manage software | yes |
| [udisks2](the-udisks2-interface.md) | access the UDisks2 service | Storage | no |
| [uhid](the-uhid-interface.md) | create kernel UID devices from user-space | Hardware, Kernel, System | no |
| [uinput](the-uinput-interface.md) | allows write access to /dev/uinput | Super privileged, Hardware | no |
| [uio](the-uio-interface.md) | access uio devices | Hardware, System | no |
| [unity7](the-unity7-interface.md) | access legacy desktop resources from Unity7 | Display | yes |
| [unity8](the-unity8-interface.md) | share data with other Unity 8 apps | Display | yes |
| [unity8-calendar](the-unity8-calendar-interface.md) | read/change shared calendar events in Ubuntu Unity 8 | Personal data | no |
| [unity8-contacts](the-unity8-contacts-interface.md) | read/change shared contacts in Ubuntu Unity 8 | Personal data | no |
| [upower-observe](the-upower-observe-interface.md) | access battery level and power usage | System, Power | yes |
| [vcio](the-vcio-interface.md) | access a Raspberry Pi's VideoCore multimedia processor | Video, Graphics, Ubuntu Core | no |
| [wayland](the-wayland-interface.md) | access compositors providing the Wayland protocol | Display | yes |
| [x11](the-x11-interface.md) | monitor mouse/keyboard input and graphics output of other apps | Display | yes |