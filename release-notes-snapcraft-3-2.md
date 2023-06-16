.. 10723.md

.. _release-notes-snapcraft-3-2:

# Release notes: Snapcraft 3.2

These are the release notes for [Snapcraft 3.2](https://github.com/snapcore/snapcraft/releases/tag/3.2), which includes new features and essential bug fixes.

For general details, including installation instructions, see [Snapcraft overview](/t/snapcraft-overview/8940), or take a look at [Snapcraft release notes](/t/snapcraft-release-notes/10721) for other *Snapcraft* releases.

## New in this release

## stage-snaps

This feature is equivalent to the [stage-packages](/t/snapcraft-parts-metadata/8336) keyword, but instead of using packages from the build environment's repositories, it uses snaps hosted on the [Snap Store](https://snapcraft.io/store).

The semantics are the same as those for `build-snaps`; when declaring a snap to be staged, the snap will be retrieved from the *Snap Store* and unpacked into the snap being built.

The `meta` and `snap` directories from the snap will be available as `meta.<snap-name>` and `snap.<snap-name>` for cases where assets from those locations are desired for reuse.

### Schema migrated from yaml to json

This makes our scheme easier to reuse in editors such as [Visual Studio Code](https://snapcraft.io/vscode) with syntax and error highlighting in-place.

See [Snapcraft scheme validation in VSCode](https://forum.snapcraft.io/t/snapcraft-schema-validation-in-vscode/9609) for an early preview.

### New colcon plugin

This plugin enables the new build system that targets [ROS2](/t/ros2-applications/7823). It's currently classed as *experimental*, as the build system is actively being worked on by the [Open Source Robotics Foundation](https://www.openrobotics.org/).

These are the options the plugin offers for a part needing to build with `colcon`:

```no-highlight
    - colcon-packages:
      (list of strings)
      List of colcon packages to build. If not specified, all packages in the
      workspace will be built. If set to an empty list ([]), no packages will
      be built, which could be useful if you only want ROS debs in the snap.
    - colcon-source-space:
      (string)
      The source space containing colcon packages (defaults to 'src').
    - colcon-rosdistro:
      (string)
      The ROS distro to use. Available options are bouncy and crystal (defaults to
      crystal), both of which are only compatible with core18 as the base.
    - colcon-cmake-args:
      (list of strings)
      Arguments to pass to cmake projects. Note that any arguments here which match
      colcon arguments need to be prefixed with a space. This can be done by quoting
      each argument with a leading space.
    - colcon-catkin-cmake-args:
      (list of strings)
      Arguments to pass to catkin packages. Note that any arguments here which match
      colcon arguments need to be prefixed with a space. This can be done by quoting
      each argument with a leading space.
    - colcon-ament-cmake-args:
      (list of strings)
      Arguments to pass to ament_cmake packages. Note that any arguments here which
      match colcon arguments need to be prefixed with a space. This can be done by
      quoting each argument with a leading space.

```

## Full list of changes

The issues and features worked on for 3.2 can be seen on the [3.2](https://bugs.launchpad.net/snapcraft/+milestone/3.2) launchpad milestone which are reflected in the following change list:

[details=List of changes for Snapcraft 3.2]

-   many: support for stage-snaps ([#2468](https://github.com/snapcore/snapcraft/pull/2468)) (LP: #1805214)
-   project loader: do not leak a part's build-environment ([#2472](https://github.com/snapcore/snapcraft/pull/2472)) (LP: #1815658)
-   build providers: remove dead code ([#2474](https://github.com/snapcore/snapcraft/pull/2474))
-   tests: disable spread colcon tests ([#2476](https://github.com/snapcore/snapcraft/pull/2476))
-   ci: shallow clones for CLA checks on travis ([#2477](https://github.com/snapcore/snapcraft/pull/2477))
-   meta: handle symlinked hooks ([#2478](https://github.com/snapcore/snapcraft/pull/2478))
-   project loader: remove special LD_LIBRARY_FLAGS handling for classic ([#2485](https://github.com/snapcore/snapcraft/pull/2485)) (LP: #1817300)
-   sources: avoid marking changes to the snap directory as dirty ([#2475](https://github.com/snapcore/snapcraft/pull/2475)) (LP: #1806746, #1816397)
-   cli: clean up snapcraft push output ([#2469](https://github.com/snapcore/snapcraft/pull/2469)) (LP: #1804439)
-   cli: handle legitimate provider exec errors ([#2483](https://github.com/snapcore/snapcraft/pull/2483))
-   schema: convert yaml jsonschema document to a json equivalent ([#2448](https://github.com/snapcore/snapcraft/pull/2448))
-   tests: make before/after items an array in schema test ([#2465](https://github.com/snapcore/snapcraft/pull/2465))
-   ruby plugin: support new download URL ([#2466](https://github.com/snapcore/snapcraft/pull/2466)) (LP: #1815336)
-   colcon plugin: new plugin ([#2456](https://github.com/snapcore/snapcraft/pull/2456)) (LP: #1805213)
-   colcon plugin: support build-time chaining ([#2486](https://github.com/snapcore/snapcraft/pull/2486)) (LP: #1816565)

[/details]