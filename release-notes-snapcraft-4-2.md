.. 19644.md

.. _release-notes-snapcraft-4-2:

# Release notes: Snapcraft 4.2

The team behind Snapcraft is pleased to announce the release of [Snapcraft 4.2](https://github.com/snapcore/snapcraft/releases/tag/4.2).

Highlights for this release include:
* new ROS 2 (Foxy Fitzroy) support
* cmake Ninja generator with `core20`
* improved track and channel listing

For general details, including installation instructions, see [Snapcraft overview](https://forum.snapcraft.io/t/snapcraft-overview/8940), or take a look at [Snapcraft release notes](https://forum.snapcraft.io/t/snapcraft-release-notes/10721) for other  *Snapcraft*  releases.

Special thanks to the contributors that helped to make this release happen: [@GamePad64](https://github.com/GamePad64), [@Saviq](https://github.com/Saviq), [@cjp256](https://github.com/cjp256), [@igorljubuncic](https://github.com/igorljubuncic) and [@sergiusens](https://github.com/sergiusens).

## New Features

### ROS 2 Foxy Fitzroy extension and updated colcon plugin

Snapcraft 4.2 includes experimental support for Robot Operating System  (ROS 2) [Foxy Fitzroy LTS](https://index.ros.org/doc/ros2/Releases/Release-Foxy-Fitzroy)  with a new [extension](/t/the-ros2-foxy-extension/19639) and colcon plugin when used with [`core20`](/t/base-snaps/11198).

For example, ROS 2 applications can now be built with a  `snapcraft.yaml` as simple as:

```yaml
name: ros2-talker-listener
version: '0.1'
summary: ROS2 Talker/Listener Example
description: |
  This example launches a ROS2 talker and listener.

grade: devel
confinement: strict
base: core20

parts:
  ros-demos:
    plugin: colcon
    source: https://github.com/ros2/demos.git
    source-branch: foxy
    source-subdir: demo_nodes_cpp
    build-packages: [make, gcc, g++]
    stage-packages: [ros-foxy-ros2launch]

apps:
  ros2-talker-listener:
    command: opt/ros/foxy/bin/ros2 launch demo_nodes_cpp talker_listener.launch.py
    plugs: [network, network-bind]
    extensions: [ros2-foxy]
```

For a walkthrough on how to work with the plugin and extension, see [https://snapcraft.io/blog/how-to-build-a-snap-using-ros-2-foxy](https://snapcraft.io/blog/how-to-build-a-snap-using-ros-2-foxy).

### Ninja file generation with cmake

By default, the [cmake plugin](t/the-cmake-plugin/8621) creates a Makefile when used with with  [`core20`](/t/base-snaps/11198) . This release adds the `cmake-generator` plugin property to optionally generate of a Ninja file:

```yaml
hello:
    source: .
    plugin: cmake
    cmake-parameters:
      - -DCMAKE_INSTALL_PREFIX=/usr
    cmake-generator: Ninja
```
### List channel tracks from Snapcraft

You can now view the available [channel tracks](/t/using-tracks/6230) for a given snap with the new `snapcraft list-tracks <snap-name>` command (or with its alias, _tracks_).

The command output shows a list of tracks together with their status, creation date, and assigned version pattern, which is required by a given snap revision to be able to release to a given track:


```bash
Name    Status    Creation-Date    Version-Pattern
latest  default   -                -
```

_Status_ can be one of the following:
* default (implicit active)
* active
* hidden
* closed

## Bug Fixes

* meta: detailed warnings for resolution of commands [@cjp256](https://github.com/cjp256) ([#3219](https://github.com/snapcore/snapcraft/pull/3219))
* file utils: introduce get_host_tool_path() to find commands on host [@cjp256](https://github.com/cjp256) ([#3244](https://github.com/snapcore/snapcraft/pull/3244))
* plugins v2: use repo.Repo not repo.Ubuntu in colcon [@cjp256](https://github.com/cjp256) ([#3257](https://github.com/snapcore/snapcraft/pull/3257))
* remote-build: use requests.get() instead of urlopen() [@cjp256](https://github.com/cjp256) ([#3255](https://github.com/snapcore/snapcraft/pull/3255))
* spread tests: fix classic patchelf linker regex to match all arches [@cjp256](https://github.com/cjp256) ([#3247](https://github.com/snapcore/snapcraft/pull/3247))
* tests: restrict colcon / ros2-foxy test to amd64 & arm64 [@cjp256](https://github.com/cjp256) ([#3254](https://github.com/snapcore/snapcraft/pull/3254))
* extensions: prepend the snapd glvnd path [@Saviq](https://github.com/Saviq) ([#3253](https://github.com/snapcore/snapcraft/pull/3253))
* build providers: honour http proxy settings for snapd [@cjp256](https://github.com/cjp256) ([#3251](https://github.com/snapcore/snapcraft/pull/3251))
* snapcraft: use system certificates by default for https requests [@cjp256](https://github.com/cjp256) ([#3252](https://github.com/snapcore/snapcraft/pull/3252))

## Specification and documentation changes

* tiny typo fix [@igorljubuncic](https://github.com/igorljubuncic) ([#3249](https://github.com/snapcore/snapcraft/pull/3249))
* experimental ros2 extension & colcon v2 plugin [@cjp256](https://github.com/cjp256) ([#3203](https://github.com/snapcore/snapcraft/pull/3203))