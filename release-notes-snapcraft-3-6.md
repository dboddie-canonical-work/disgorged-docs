.. 11898.md

.. _release-notes-snapcraft-3-6:

# Release notes: Snapcraft 3.6

These are the release notes for [Snapcraft 3.6](https://github.com/snapcore/snapcraft/releases/tag/3.6).

This is a minor release to fix some outstanding issues and to add an improvement to the *ant* plugin.

For general details, including installation instructions, see [Snapcraft overview](snapcraft-overview.md), or take a look at [Snapcraft release notes](snapcraft-release-notes.md) for other *Snapcraft* releases.

## New *core* features

### Updates to the [ant](the-ant-plugin.md) plugin

It is now possible to specify the build file location with the `ant-buildfile` keyword.

## Full list of changes

The issues and features worked on for 3.6 can be seen on the [3.6](https://github.com/snapcore/snapcraft/releases/tag/3.6) launchpad milestone which are reflected in the following change list:

[details=List of changes for Snapcraft 3.6]

#### Sergio Schvezov

-   docker images: update to be self contained ([#2591](https://github.com/snapcore/snapcraft/pull/2591))
-   static: update to newer black ([#2599](https://github.com/snapcore/snapcraft/pull/2599))
-   repo: set priority to critical for debs (LP: #1821313)

#### Kyle Fazzari

-   docker images: use build stages and generate locale ([#2588](https://github.com/snapcore/snapcraft/pull/2588))
-   {catkin,colcon} plugin: remove old ROS key ([#2586](https://github.com/snapcore/snapcraft/pull/2586))
-   catkin plugin: check workspace for dependencies ([#2585](https://github.com/snapcore/snapcraft/pull/2585)) (LP: #1832044)

#### Stefan Bodewig

-   ant plugin: make build file location configurable ([#2596](https://github.com/snapcore/snapcraft/pull/2596))

#### Chris Patterson

-   tools: add `black` snap to environment-setup.sh ([#2595](https://github.com/snapcore/snapcraft/pull/2595))



[/details]