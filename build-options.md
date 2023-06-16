.. 14250.md

.. _build-options:

# Build options

By default, [Snapcraft](/t/snapcraft-overview/8940) uses [LXD](https://linuxcontainers.org/lxd/introduction/) or [Multipass](https://multipass.run/) to simplify the build process and to confine the build environment within a virtual machine. For most developers, this happens transparently and is the best way to build snaps.

But to cater for different operating systems, environments and requirements, Snapcraft also offers a number of flexible options for how it can be run. These are outlined below.

## Currently supported

| Command | Description | Requirements |
|-|-|-|
| `snapcraft` <br> _default_ |  Uses [LXD or Multipass](t/iterating-over-a-build/12143) to builds the snap within an instantiated VM to ensure a clean, isolated, build environment. Nested VMs require accelerated/nested VM functionality.  | Any supported system with VM capabilities. |
| `snapcraft remote-build` | [Remote build](/t/remote-build/14400) runs a multi-architecture build process on remote servers using [Launchpad](https://launchpad.net/). | Prospective snaps need to be open source as the code will be publicly available, plus a [Launchpad account](https://login.launchpad.net/+new_account).|
| Build from GitHub | [Build from GitHub](/t/build-from-github/26004) is another remote build option,  triggering automatic snap builds from your developer account. | Requires snap source hosted on a public GitHub repository, and account linking between GitHub and your developer account.|
| `electron-builder -l snap` | **[Electron builder integration](/t/electron-apps/6748)** enables Electron app developers to easily create snaps with a simple modification to `package.json `. | Requires [Electron-builder](https://www.electron.build/) with Linux or macOS *snapcraft* from the Snap Store  or [brew](https://brew.sh/). |

Snaps build on the bases `core`, `core18`, and `core20` default to using Multipass as the build provider.  `core22` snaps use LXD on linux systems.  Other systems (macOS and Windows) use Multipass.

> ⓘ See [this page](/t/build-on-lxd/4157) for details on how to configure snapcraft to use either LXD or Multipass and other build provider-specific details.

<h2 id='heading--snapcraft'>Build environment options</h2>

Snapcraft can optionally use the following arguments to modify the build environment.

| Snapcraft argument | Description | Requirements |
|-|-|-|
|  `--destructive-mode` | **Destructive mode**. Designed to be used in temporary/short-lived environments, such as on a CI system, because the build _could_ contaminate the host build environment. | Needs access to Ubuntu 18.04 (core18) or 16.04 (core16 / core), alongside *snapcraft*, from the Snap Store. |
| `--use-lxd` | **[LXD container](/t/build-on-lxd/4157)**. Builds the snap using [LXD](https://linuxcontainers.org/lxd/introduction/), rather than Multipass. This can potentially reduce resource usage, especially from a VM. </br> Set `SNAPCRAFT_BUILD_ENVIRONMENT=lxd` to use LXD by default. | Requires LXD|
| `--http-proxy <http-proxy>` | Configures HTTP proxy.  Snapcraft will honour `http_proxy` environment flag as well.  | None |
| `--https-proxy <https-proxy>` | Configures HTTPS proxy.  Snapcraft will honour `https_proxy` environment flag as well.  | None |
| `--add-ca-certificates <path>` | Adds trusted CAs in Snapcraft-created build environments. May be a CA certificate file or directory containing certificate files.</br> [Not currently compatible with Snapcraft 7.x](https://bugs.launchpad.net/snapcraft/+bug/2004072) | LXD, Multipass |
| `--bind-ssh` | Bind ~/.ssh directory to local build instance. | LXD, Multipass |
| `--ua-token` | Configure build environment with ESM using specified UA token. | LXD, Multipass |
| `--enable-manifest` | Add the build manifest to the snap package in `snap/manifest.yaml`. This contains the specific sources and packages used to build the snap and allows the Snap Store to [automatically check your Snap for security issues](https://snapcraft.io/blog/introducing-developer-notifications-for-snap-security-updates). This is identical to setting the environment variable `SNAPCRAFT_BUILD_INFO=1`. Snaps built on Launchpad will have this set automatically. | None |

<h2 id='heading--deprecated'>Deprecated build options</h2>

| Command | Description | Requirements |
|-|-|-|
| `snapcraft cleanbuild` | **Cleanbuild**. Legacy non-bases method for building snaps in a LXD container. | Deprecated with the release of [Snapcraft 3.x](https://forum.snapcraft.io/t/release-notes-snapcraft-3-0/10704) and no longer supported. |
| `apt install snapcraft` | **Snapcraft _deb_ package**. Originally used to install *snapcraft* on Ubuntu-based Linux distributions (and Debian). | Outdated and no longer supported. See [Snapcraft overview](/t/snapcraft-overview/8940) for current installation instructions.|
| `snapcraft --offline` | Allow snapcraft to build snaps on a system without a network connection provided that 1) the build environment is prepared, and 2) all sources and packages required by the parts are already on the local system (that usually means that `snapcraft pull` was successfully executed when networking was still available). | None |

A *supported Linux system* is a host or VM running a snap-capable Linux distribution. See [Installing snapd](/t/installing-snapd/6735) for details.