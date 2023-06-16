.. 22788.md

.. _release-notes-snapcraft-4-5-1:

# Release notes: Snapcraft 4.5.1

The team behind Snapcraft is pleased to announce the release of [Snapcraft 4.5.1](https://github.com/snapcore/snapcraft/releases/tag/4.5.1).

Highlights for this release include:

* more improvements for using python3.8 from within a snap
* allow revoking validation assertions
* experimental notice for compression has been removed
* SDK snap paths in ACLOCAL_PATH are now included

For general details, including installation instructions, see [Snapcraft overview](https://forum.snapcraft.io/t/snapcraft-overview/8940), or take a look at [Snapcraft release notes](https://forum.snapcraft.io/t/snapcraft-release-notes/10721) for other  *Snapcraft*  releases.

## Full list of changes

The issues and features worked on for Snapcraft 4.5 are reflected in the following change list:

[details=List of changes for Snapcraft 4.5.1]
</br>
-   More improvements for using python3.8 from within a snap [@kenvandine](https://github.com/kenvandine) ([#3430](https://github.com/snapcore/snapcraft/pull/3430))
-   Allow revoking validation assertions (LP: #1912332) [@nessita](https://github.com/nessita) ([#3433](https://github.com/snapcore/snapcraft/pull/3433))
-   spread tests: remove legacy plugin tests [@cjp256](https://github.com/cjp256) ([#3432](https://github.com/snapcore/snapcraft/pull/3432))
-   godeps spread test: use latest/stable go snap [@cjp256](https://github.com/cjp256) ([#3431](https://github.com/snapcore/snapcraft/pull/3431))
-   plugins v1: Pin pip to supported versions [@philroche](https://github.com/philroche) ([#3428](https://github.com/snapcore/snapcraft/pull/3428))
-   cli: remove experimental notice for compression [@cjp256](https://github.com/cjp256) ([#3421](https://github.com/snapcore/snapcraft/pull/3421))
-   Ensure PYTHONPATH is appropriate for building packages with gnome-3-38 [@kenvandine](https://github.com/kenvandine) ([#3424](https://github.com/snapcore/snapcraft/pull/3424))
-   Ensure PYTHONPATH is properly set for gnome-3-34 builds [@kenvandine](https://github.com/kenvandine) ([#3426](https://github.com/snapcore/snapcraft/pull/3426))
-   Revert "cli: allow validation assertions to be revoked ([#3417](https://github.com/snapcore/snapcraft/pull/3417))" [@sergiusens](https://github.com/sergiusens) ([#3422](https://github.com/snapcore/snapcraft/pull/3422))
-   Include SDK snap paths in ACLOCAL_PATH [@kenvandine](https://github.com/kenvandine) ([#3419](https://github.com/snapcore/snapcraft/pull/3419))
-   plainbox spread tests: set tasks to manual [@cjp256](https://github.com/cjp256) ([#3420](https://github.com/snapcore/snapcraft/pull/3420))
[/details]