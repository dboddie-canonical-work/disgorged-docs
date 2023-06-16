.. 23145.md

.. _release-notes-snapcraft-4-5-4:

# Release notes: Snapcraft 4.5.4

The team behind Snapcraft is pleased to announce the release of [Snapcraft 4.5.4](https://github.com/snapcore/snapcraft/releases/tag/4.5.4).

Highlights for this release include:

* more updates to the Python v2 plugin
* default python-packages to [pip, setuptools, wheel]
* updated electron-builder test

For general details, including installation instructions, see [Snapcraft overview](https://forum.snapcraft.io/t/snapcraft-overview/8940), or take a look at [Snapcraft release notes](https://forum.snapcraft.io/t/snapcraft-release-notes/10721) for other  *Snapcraft*  releases.

## Full list of changes

The issues and features worked on for this release are reflected in the following change list:

[details=List of changes for Snapcraft 4.5.4]
</br>
-   python v2 plugin: fix multiple python parts with staged python [@cjp256](https://github.com/cjp256) ([#3451](https://github.com/snapcore/snapcraft/pull/3451))
-   python v2 plugin: filter set options to reduce output noise [@cjp256](https://github.com/cjp256) ([#3455](https://github.com/snapcore/snapcraft/pull/3455))
-   python v2 plugin: reduce noise by replacing for-loop with xargs [@cjp256](https://github.com/cjp256) ([#3456](https://github.com/snapcore/snapcraft/pull/3456))
-   extensions: check that the platform snap is connected in desktop extensions and bail out if not [@oSoMoN](https://github.com/oSoMoN) ([#3437](https://github.com/snapcore/snapcraft/pull/3437))
-   spread: update electron-builder test [@sergiusens](https://github.com/sergiusens) ([#3454](https://github.com/snapcore/snapcraft/pull/3454))
-   python v2 plugin: default python-packages to [pip, setuptools, wheel] [@cjp256](https://github.com/cjp256) ([#3453](https://github.com/snapcore/snapcraft/pull/3453))
-   storeapi: rename SCA to DashboardAPI [@sergiusens](https://github.com/sergiusens) ([#3450](https://github.com/snapcore/snapcraft/pull/3450))
-   storeapi: rename SnapClientIndex to SnapAPI [@sergiusens](https://github.com/sergiusens) ([#3448](https://github.com/snapcore/snapcraft/pull/3448))
-   ci: don't publish snap on push to master [@cjp256](https://github.com/cjp256) ([#3449](https://github.com/snapcore/snapcraft/pull/3449))
[/details]