.. 7744.md

.. _supported-interfaces:

# Supported interfaces

Interfaces enable resources from one snap to be shared with another and with the system. For a snap to use an interface, its developer needs to have first defined its corresponding plugs and slots within a snap's [snapcraft.yaml](/t/creating-snapcraft-yaml/11666) file.

> ℹ For details on how to add an interface to your own snap, see [Snapcraft interfaces](/t/snapcraft-interfaces/13123). For general usage details, see [Interface management](/t/interface-management/6154).

The table below lists currently supported interfaces, with links to further details for each interface.

The following column names are used:

- **Interface** is the syntactical interface name, as used by snaps.

- **Description** is a brief overview of what the interface permits. Select the interface name to open the interface-specific page for a more detailed description on each interface.

- **Categories** are used to split interfaces into broad types, and also to indicate what kind of access they permit. Video, graphics and audio are typical desktop requirements, for example, while VM, Container, Kernel and Developer imply more specific roles. The Ubuntu Core category is used to denote when an interface is intended for [Ubuntu Core](https://forum.snapcraft.io/t/glossary/14612#heading--ubuntu-core), and _Super privileged_ is used when an interface requires extra security scrutiny. See [Super-privileged interfaces](/t/super-privileged-interfaces/34740) for more information.

- **Auto-connect** indicates that the interface will be connected by default when the snap is first installed, requiring no further user action. If `Auto-connect=no`, an interface can still be automatically connected if the snap developer has requested, and been granted, explicit permission. See [Interface connection mechanism](/t/the-interface-connection-mechanism/20179) for details.

 **Important:** if a snap is installed prior to an interface being granted auto-connect permission, and permission is subsequently granted and the snap updated, when the installed snap updates, the interface will be auto-connected.

| Interface | Description | Categories | Auto-connect |
|---|----|---|---|
| [account-control](/t/the-account-control-interface/7746) | add/remove user accounts or change passwords | System, Account | no |
| [accounts-service](/t/the-accounts-service-interface/7802) | allows communication with the accounts service | System, Account | no |
| [acrn](/t/the-acrn-interface/30982) | allows access to user VMs using the ACRN hypervisor | VM, Hypervisor, Developer | no |
| [adb-support](/t/the-adb-support-interface/9720) | allows operating as Android Debug Bridge service | ADB, Developer | no |
| [allegro-vcu](/t/the-allegro-vcu-interface/26452) | access the Allegro Video Core Unit | Video, Graphics | no |
| [alsa](/t/the-alsa-interface/7766) | play or record sound | Audio | no |
| [appstream-metadata](/t/the-appstream-metadata-interface/13050) | allows access to AppStream metadata | System, Developer, Manage software | no |
| [audio-playback](/t/the-audio-playback-interface/13089) | allows audio playback via supporting services | Audio, Playback | yes |
| [audio-record](/t/the-audio-record-interface/13090) | allows audio recording via supported services | Audio, Record | no |
| [autopilot-introspection](/t/the-autopilot-introspection-interface/7768) | be controlled by Autopilot software | System, Developer | no |
| [avahi-control](/t/the-avahi-control-interface/7769) | advertise services over the local network | Network, Local network, Nearby devices | no |
| [avahi-observe](/t/the-avahi-observe-interface/7770) | detect services and devices over the local network | Network, Local network, Nearby devices | no |
| [block-devices](/t/the-block-devices-interface/9721) | access to disk block devices | Super privileged, Storage, Low level | no |
| [bluetooth-control](/t/the-bluetooth-control-interface/7771) | access Bluetooth hardware directly | Network, Bluetooth, Nearby devices | no |
| [bluez](/t/the-bluez-interface/7772) | use Bluetooth devices | Network, Bluetooth, Nearby devices | no |
| [bool-file](/t/the-bool-file-interface/7803) | allows access to specific file with bool semantics | System, Low level, Privileged | no |
| [broadcom-asic-control](/t/the-broadcom-asic-control-interface/7773) | control Broadcom network switches | Network, System | no |
| [browser-support](/t/the-browser-support-interface/7775) | use functions essential for Web browsers | Browser, Network | no when allow-sandbox: true, yes otherwise |
| [calendar-services](/t/the-calendar-service-interface/7804) | allows communication with Evolution Data Server calendar | Personal data, Contacts and calendar | no |
| [camera](/t/the-camera-interface/7776) | use your camera or webcam | Camera, Personal data | no |
| [can-bus](/t/the-can-bus-interface/7805) | allows access to the CAN bus | System, Developer | no |
| [cifs-mount](/t/the-cifs-mount-interface/13091) | allows the mounting and unmounting of CIFS filesystems | Storage | no |
| [classic-support](/t/the-classic-support-interface/7777) | enable resource access to classic snap | Super privileged, Ubuntu Core | no |
| [contacts-service](/t/the-contacts-service-interface/13092) | allows communication with the Evolution Data Server address book | Personal data, Contacts and calendar | no |
| [content](/t/the-content-interface/1074) | access resources across snaps | Storage, Files, Attributes | yes for snaps from same publisher, no otherwise |
| [core-support](/t/the-core-support-interface/7778) | deprecated since snap 2.34 | System, Other | no |
| [cpu-control](/t/the-cpu-control-interface/7780) | set certain CPU values | System, Developer | no |
| [cups](/t/the-cups-interface/26453) | access to the CUPS socket for printing | Printing | not applicable |
| [cups-control](/t/the-cups-control-interface/7779) | print documents | Printing | no |
| [custom-device](/t/the-custom-device-interface/29487) | permits access to a specific class of device | Super privileged, Ubuntu Core | no |
| [daemon-notify](/t/the-daemon-notify-interface/7809) | allows sending daemon status changes to service manager | System, Developer | no |
| [dbus](/t/the-dbus-interface/2038) | allow snaps to communicate over D-Bus | System, Developer | no |
| [dcdbas-control](/t/the-dcdbas-control-interface/7781) | shut down or restart Dell devices | Developer | no |
| [desktop](/t/the-desktop-interface/7783) | provides access to common desktop elements | Desktop | yes |
| [desktop-launch](/t/the-desktop-launch-interface/25495) | identify and launch desktop apps from other snaps | Super privileged, Desktop | no |
| [desktop-legacy](/t/the-desktop-legacy-interface/7782) | enables the use of legacy desktop methods (including input method and accessibility services) | Desktop | yes |
| [device-buttons](/t/the-device-buttons-interface/8598) | use any device-buttons | Hardware, Developer | no |
| [display-control](/t/the-display-control-interface/9723) | allows configuring display parameters | Display, Graphics | no |
| [dm-crypt](/t/the-dm-crypt-interface/26487) | access encrypted storage devices | Super privileged, Ubuntu Core, Storage | no |
| [docker](/t/the-docker-interface/7787) | start, stop, or manage Docker containers | Super privileged, Containers | no |
| [docker-support](/t/the-docker-support-interface/7810) | allows operating as the Docker daemon | Super privileged, Containers | no |
| [dsp](/t/the-dsp-interface/25491) | enables the control of digital signal processors (DSPs) | Hardware, Developer | no |
| [dummy](/t/the-empty-interface/7811) | renamed to empty interface | System, Other | no |
| [dvb](/t/the-dvb-interface/7812) | allows access to all DVB devices and APIs | Hardware, Developer | no |
| [empty](/t/the-empty-interface/7811) | allows testing without additional permissions | System, Other | no |
| [firewall-control](/t/the-firewall-control-interface/7813) | configure a network firewall | Networking | no |
| [fpga](/t/the-fpga-interface/26498) | permits access to an FPGA subsystem | Hardware, Developer | no |
| [framebuffer](/t/the-framebuffer-interface/7814) | access to universal framebuffer devices | Hardware, Developer | no |
| [fuse-support](/t/the-fuse-support-interface/7816) | enables access to the FUSE filesystems | Storage | no |
| [fwupd](/t/the-fwupd-interface/7825) | allows operating as the fwupd service | System, Security, Firmware | no |
| [gconf](/t/the-gconf-interface/26499) | access the legacy GConf config system | System, Developer, Settings | no |
| [gpg-keys](/t/the-gpg-keys-interface/7827) | read GPG user configuration and keys | GPG, Personal data, Security | no |
| [gpg-public-keys](/t/the-gpg-public-keys-interface/7828) | read GPG non-sensitive configuration and public keys | GPG, Personal data, Security | no |
| [gpio](/t/the-gpio-interface/7829) | access specific GPIO pins | GPIO, Hardware, Developer | no |
| [gpio-control](/t/the-gpio-control-interface/13037) | allows to export/unexport and control all GPIOs | Super privileged, GPIO | no |
| [gpio-memory-control](/t/the-gpio-memory-control-interface/7830) | allows write access to all GPIO memory | GPIO, Hardware, Developer | no |
| [greengrass-support](/t/the-greengrass-support-interface/7831) | allows operating as the Greengrass service | Super privileged, Edge, AWS, Discrete | no |
| [gsettings](/t/the-gsettings-interface/7832) | provides access to any GSettings item for current user | System, Developer, Settings | yes |
| [hardware-observe](/t/the-hardware-observe-interface/7833) | access hardware information | System, Hardware | no |
| [hardware-random-control](/t/the-hardware-random-control-interface/7835) | provide entropy to hardware random number generator | System, Hardware | no |
| [hardware-random-observe](/t/the-hardware-random-observe-interface/7836) | use hardware-generated random numbers | System, Hardware | no |
| [hidraw](/t/the-hidraw-interface/7837) | access hidraw devices | System | no |
| [home](/t/the-home-interface/7838) | access non-hidden files in the home directory | Storage, Personal data | yes on classic (traditional distributions), no otherwise |
| [hostname-control](/t/the-hostname-control-interface/7841) | allows configuring the system hostname | Networking | no |
| [hugepages-control](/t/the-hugepages-control-interface/26501) | control HugePages memory blocks | System, Memory, Kernel | no |
| [i2c](/t/the-i2c-interface/7842) | access i²c devices | System, Hardware | no |
| [iio](/t/the-iio-interface/7846) | access IIO devices | System, Hardware | no |
| [intel-mei](/t/the-intel-mei-interface/10203) | access to the Intel MEI management interface | System, Firmware | no |
| [io-ports-control](/t/the-io-ports-control-interface/7848) | allows access to all I/O ports | System, | no |
| [ion-memory-control](/t/the-ion-memory-control-interface/26502) | access Android's ION memory allocator | System  | no |
| [jack1](/t/the-jack1-interface/13093) | allows interaction with the JACK audio connection server | Audio | no |
| [joystick](/t/the-joystick-interface/7849) | use any connected joystick | Hardware, Developer | no |
| [juju-client-observe](/t/the-juju-client-observe-interface/7850) | read the Juju client configuration | Developer, Discrete | no |
| [kernel-crypto-api](/t/the-kernel-crypto-api-interface/26503) | read and manage kernel supported crypto ciphers | System, Kernel, Security | no |
| [kernel-module-control](/t/the-kernel-module-control-interface/7853) | insert, remove and query kernel modules | Super priviliged, System, Kernel | no |
| [kernel-module-load](/t/the-kernel-module-load-interface/28298) | load, or deny loading, specific kernel modules | Super priviliged, System, Kernel | no |
| [kernel-module-observe](/t/the-kernel-module-observe-interface/9719) | query kernel modules | System, Kernel | no |
| [kubernetes-support](/t/the-kubernetes-support-interface/7855) | use functions essential for Kubernetes | Super priviliged, Hypervisor, Discrete | no |
| [kvm](/t/the-kvm-interface/7856) | allows access to the kvm device | VM, Hypervisor, Developer | no |
| [libvirt](/t/the-libvirt-interface/7858) | provides access to the libvirt service | VM, Hypervisor, Developer | no |
| [locale-control](/t/the-locale-control-interface/7859) | change system language and region settings | Language and region, Personalisation | no |
| [location-control](/t/the-location-control-interface/7860) | allows operating as the location service | Location | no |
| [location-observe](/t/the-location-observe-interface/7861) | access your location | Location | no |
| [log-observe](/t/the-log-observe-interface/7862) | read system logs | System, Developer | no |
| [login-session-control](/t/the-login-session-control-interface/13094) | allows setup of login sessions and grants privileged access to user sessions | System, Security | no |
| [login-session-observe](/t/the-login-session-observe-interface/14580) | allows reading login and session information | System, Security | no |
| [lxd](/t/the-lxd-interface/7863) | provides access to the LXD socket | Super privileged, Container, Discrete | no |
| [lxd-support](/t/the-lxd-support-interface/7864) | allows operating as the LXD service | Super privileged, Container, Discrete | no |
| [maliit](/t/the-maliit-interface/7872) | use an on-screen keyboard | Developer | no |
| [media-control](/t/the-media-control-interface/26504/) | access media control devices and Video4Linux (V4L) devices | Hardware, Developer, Video | no |
| [media-hub](/t/the-media-hub-interface/7873) | access snaps providing the media-hub interface | Developer, Media | yes |
| [microstack-support](/t/the-microstack-support-interface/26505/) | multiple service access to the Microstack infrastructure | Super privileged, Container, Discrete | no |
| [mir](/t/the-mir-interface/7874) | enables access to the Mir display service | Display | yes |
| [modem-manager](/t/the-modem-manager-interface/7875) | use and configure modems | Networking | no |
| [mount-control](/t/the-mount-control-interface/28953) | mount and unmount transient and persistent filesystem mount points | Super privileged, Storage | no |
| [mount-observe](/t/the-mount-observe-interface/7876) | read mount table and quota information | Storage | no |
| [mpris](/t/the-mpris-interface/7877) | media key control of music and video players | Sound | no |
| [multipass-support](/t/the-multipass-support-interface/13095) | multipass-support allows operating as the Multipass service | Super privileged, VM, Discrete | no |
| [netlink-audit](/t/the-netlink-audit-interface/7878) | allows access to kernel audit system through Netlink | Inter-process communication (IPC), Netlink, Developer | no |
| [netlink-connector](/t/the-netlink-connector-interface/7879) | communicate through the kernel Netlink connector | Inter-process communication (IPC), Netlink, Developer | no |
| [netlink-driver](/t/the-netlink-driver-interface/25485) | operate a kernel driver module exposed via Netlink | Inter-process communication (IPC), Netlink, Developer | no |
| [network](/t/the-network-interface/7880) | enables network access | Networking | yes |
| [network-bind](/t/the-network-bind-interface/7881) | operate as a network service | Networking | yes |
| [network-control](/t/the-network-control-interface/7882) | change low-level network settings | Networking | no |
| [network-manager](/t/the-network-manager-interface/7883) | configure and observe networking via NetworkManager | Networking | no |
| [network-manager-observe](/t/the-network-manager-observe-interface/13096) | allows observing NetworkManager settings | Networking | no |
| [network-observe](/t/the-network-observe-interface/7884) | query network status information | Networking | no |
| [network-setup-control](/t/the-network-setup-control-interface/7885) | change network settings via Netplan | Networking | no |
| [network-setup-observe](/t/the-network-setup-observe-interface/7888) | read network settings | Networking | no |
| [network-status](/t/the-network-status-interface/7890) | access the NetworkingStatus service | Networking | yes |
| [ofono](/t/the-ofono-interface/7891) | allows operating as the oFono service | Networking, Discrete, Developer | no |
| [online-accounts-service](/t/the-online-accounts-service-interface/7893) | access to the Online Accounts service | Service, Developer | yes |
| [opengl](/t/the-opengl-interface/7894) | access OpenGL/GPU hardware | Display, Graphics | yes |
| [openvswitch](/t/the-openvswitch-interface/7896) | control Open vSwitch hardware | Networking, Service, Developer | no |
| [openvswitch-support](/t/the-openvswitch-support-interface/7897) | enables kernel support for Open vSwitch | Networking, Service, Developer | no |
| [optical-drive](/t/the-optical-drive-interface/7898) | read/write access to CD/DVD drives | Storage, Hardware, Developer | yes, unless drive can write |
| [packagekit-control](/t/the-packagekit-control-interface/13052) | control the PackageKit service | Super privileged, Packaging | no |
| [password-manager-service](/t/the-password-manager-service-interface/7899) | read, add, change, or remove saved passwords | System, Security | no |
| [personal-files](/t/the-personal-files-interface/9357) | read or write files in the user's home directory | Super privileged, Personal data, Attributes | no |
| [physical-memory-control](/t/the-physical-memory-control-interface/7900) | read and write memory used by any process | System, Memory, Kernel | no |
| [physical-memory-observe](/t/the-physical-memory-observe-interface/7901) | read memory used by any process | System, Memory, Kernel | no |
| [polkit](/t/the-polkit-interface/28408) | access to the polkit authorisation manager | System, Security | no |
| [posix-mq](/t/the-posix-mq-interface/31668) | enables inter-process communication (IPC) messages | Super privileged, IPC | no by default, yes with snaps from the same publisher |
| [power-control](/t/the-power-control-interface/26506) | read and write system power settings | System, Power | no |
| [ppp](/t/the-ppp-interface/7902) | access to configure and observe PPP networking | Networking | no |
| [process-control](/t/the-process-control-interface/7903) | pause or end any process on the system | System | no |
| [ptp](/t/the-ptp-interface/26565) | access to the Precision Time Protocol subsystem | System, Developer | no |
| [pulseaudio](/t/the-pulseaudio-interface/7906) | play and record sound | Audio | no |
| [pwm](/t/the-pwm-interface/25857) | access specific PWM channels | System, Developer, Hardware, WIP | no |
| [qualcomm-ipc-router](/t/the-qualcomm-ipc-router-interface/26567) | access Qualcomm IPC router sockets | IPC, Kernel, System | no |
| [raw-input](/t/the-raw-input-interface/25493) | access raw input devices directly | System, Developer, Hardware | no |
| [raw-usb](/t/the-raw-usb-interface/7908) | access USB hardware directly | System, Developer, Hardware | no |
| [raw-volume](/t/the-raw-volume-interface/14578) | access specific disk partitions | Storage | no |
| [removable-media](/t/the-removable-media-interface/7910) | read/write files on removable storage devices | Storage | no |
| [screencast-legacy](/t/the-screencast-legacy-interface/13097) | allows screen recording and audio recording alongside writing to arbitrary filesystem paths | Legacy | no |
| [screen-inhibit-control](/t/the-screen-inhibit-control-interface/7911) | prevent screen sleep, lock and screensaver | Display | yes |
| [scsi-generic](/t/the-scsi-generic-interface/28409) | read and write access to SCSI Generic driver devices | Storage | no |
| [sd-control](/t/the-sd-control-interface/25489) | control SD cards on specific devices | Super privileged, Storage | no |
| [serial-port](/t/the-serial-port-interface/7913) | access serial port hardware | System, Developer, Hardware | no by default, yes with snaps from the same publisher |
| [shared-memory](/t/the-shared-memory-interface/28382) | enables two snaps to access the same shared memory | Super privileged, IPC | no |
| [shutdown](/t/the-shutdown-interface/7914) | restart or power off the device | System, Power | no |
| [snap-refresh-control](/t/the-snap-refresh-control-interface/26569) | permits bespoke snap refresh control | Super privileged, Packaging | no |
| [snapd-control](/t/the-snapd-control-interface/7915) | install or remove software | Super privileged, Packaging | no |
| [spi](/t/the-spi-interface/7916) | access specific SPI devices | System, Developer, Hardware | no |
| [ssh-keys](/t/the-ssh-keys-interface/7917) | access SSH private and public keys | Security | no |
| [ssh-public-keys](/t/the-ssh-public-keys-interface/7918) | access SSH public keys | Security | no |
| [steam-support](/t/the-steam-support-interface/30990) | allows the Steam snap to access pressure-vessel containers | Super privileged, Discrete | no |
| [storage-framework-service](/t/the-storage-framework-service-interface/7919) | operate as, or interact with, the Storage Framework | Storage | no |
| [system-backup](/t/the-system-backup-interface/14348) | read-only access to the system for backups | Storage | no |
| [system-files](/t/the-system-files-interface/9358) | read or write files in the system | Super privileged, Storage, Attributes | no |
| [system-observe](/t/the-system-observe-interface/7921) | read process and system information | Monitoring, System | no |
| [system-packages-doc](/t/the-system-packages-doc-interface/17788) | access system documentation in /usr/share/doc | Developer | no |
| [system-source-code](/t/the-system-source-code-interface/20115) | access kernel source and headers in /usr/src | Developer | no |
| [system-trace](/t/the-system-trace-interface/7922) | monitor or control any running program | Monitoring, System | no |
| [tee](/t/the-tee-interface/26573) | permits access to the Trusted Execution Environment | Super privileged, Security, Ubuntu Core | no |
| [thumbnailer-service](/t/the-thumbnailer-service-interface/7923) | create thumbnail images from local media files | Storage, Media | no |
| [time-control](/t/the-time-control-interface/7924) | change the date and time | Time | no |
| [timeserver-control](/t/the-timeserver-control-interface/7925) | change time server settings | Time | no |
| [timezone-control](/t/the-timezone-control-interface/7926) | change the time zone | Time | no |
| [tpm](/t/the-tpm-interface/7927) | allows access to the Trusted Platform Module device | Kernel, Security | no |
| [u2f-devices](/t/the-u2f-devices-interface/9722/) | use any U2F devices | Security, Hardware, Developer | no |
| [ubuntu-download-manager](/t/the-ubuntu-download-manager-interface/7928) | use the Ubuntu Download Manager | System, Developer, Manage software | yes |
| [udisks2](/t/the-udisks2-interface/7930) | access the UDisks2 service | Storage | no |
| [uhid](/t/the-uhid-interface/7931) | create kernel UID devices from user-space | Hardware, Kernel, System | no |
| [uinput](/t/the-uinput-interface/20116) | allows write access to /dev/uinput | Super privileged, Hardware | no |
| [uio](/t/the-uio-interface/16041) | access uio devices | Hardware, System | no |
| [unity7](/t/the-unity7-interface/7786) | access legacy desktop resources from Unity7 | Display | yes |
| [unity8](/t/the-unity8-interface/7932) | share data with other Unity 8 apps | Display | yes |
| [unity8-calendar](/t/the-unity8-calendar-interface/7933) | read/change shared calendar events in Ubuntu Unity 8 | Personal data | no |
| [unity8-contacts](/t/the-unity8-contacts-interface/7934) | read/change shared contacts in Ubuntu Unity 8 | Personal data | no |
| [upower-observe](/t/the-upower-observe-interface/7935) | access battery level and power usage | System, Power | yes |
| [vcio](/t/the-vcio-interface/26575) | access a Raspberry Pi's VideoCore multimedia processor | Video, Graphics, Ubuntu Core | no |
| [wayland](/t/the-wayland-interface/7784) | access compositors providing the Wayland protocol | Display | yes |
| [x11](/t/the-x11-interface/7785) | monitor mouse/keyboard input and graphics output of other apps | Display | yes |