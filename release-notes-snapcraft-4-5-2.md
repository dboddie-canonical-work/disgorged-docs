.. 23142.md

.. _release-notes-snapcraft-4-5-2:

# Release notes: Snapcraft 4.5.2

The team behind Snapcraft is pleased to announce the release of [Snapcraft 4.5.2](https://github.com/snapcore/snapcraft/releases/tag/4.5.2).

Highlights for this release include:

* more improvements to the Python v2 plugin
* specify arch-specific bundle directories with the Flutter plugin
* build providers will now clean the build environment when the project directory changes


For general details, including installation instructions, see [Snapcraft overview](https://forum.snapcraft.io/t/snapcraft-overview/8940), or take a look at [Snapcraft release notes](https://forum.snapcraft.io/t/snapcraft-release-notes/10721) for other  *Snapcraft*  releases.

## Full list of changes

The issues and features worked on for this release are reflected in the following change list:

[details=List of changes for Snapcraft 4.5.2]
</br>
-   extensions: Fix Documents, Pictures etc symlinks [@diddledan](https://github.com/diddledan) ([#3435](https://github.com/snapcore/snapcraft/pull/3435))
-   python v2 plugin: fix typo restoring shell state [@cjp256](https://github.com/cjp256) ([#3441](https://github.com/snapcore/snapcraft/pull/3441))
-   extensions: support fontless systems in configure hook [@kenvandine](https://github.com/kenvandine) ([#3439](https://github.com/snapcore/snapcraft/pull/3439))
-   flutter: specify arch specific bundle dirs [@kenvandine](https://github.com/kenvandine) ([#3438](https://github.com/snapcore/snapcraft/pull/3438))
-   repo: apt sources management refactor [@cjp256](https://github.com/cjp256) ([#3363](https://github.com/snapcore/snapcraft/pull/3363))
-   python v2 plugin: consistent linking for interpreter [@cjp256](https://github.com/cjp256) ([#3320](https://github.com/snapcore/snapcraft/pull/3320))
-   repo: address issue with fix_symlink() when pointed at directory [@cjp256](https://github.com/cjp256) ([#3370](https://github.com/snapcore/snapcraft/pull/3370))
-   build providers: clean environment if project directory is changed [@cjp256](https://github.com/cjp256) ([#3434](https://github.com/snapcore/snapcraft/pull/3434))
[/details]