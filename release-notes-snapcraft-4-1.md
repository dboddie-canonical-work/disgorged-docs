.. 18769.md

.. _release-notes-snapcraft-4-1:

# Release notes: Snapcraft 4.1

The team behind Snapcraft is pleased to announce the release of [Snapcraft 4.1](https://github.com/snapcore/snapcraft/releases/tag/4.1).

The most interesting feature in this release is the addition a [flutter](the-flutter-plugin.md) plugin to help with the creation of snaps for Flutter based applications, and a flutter extension to help handle their dependencies.

For general details, including installation instructions, see [Snapcraft overview](snapcraft-overview.md), or take a look at [Snapcraft release notes](snapcraft-release-notes.md) for other *Snapcraft* releases.

## Full list of changes

The issues and features worked on for Snapcraft 4.1 are reflected in the following change list:

[details=List of changes for Snapcraft 4.1]
</br>

-   flutter v1 plugin: new plugin for flutter [@sergiusens](https://github.com/sergiusens) ([#3192](https://github.com/snapcore/snapcraft/pull/3192))
-   flutter v1 plugin: pull from source-subdir if set [@sergiusens](https://github.com/sergiusens) ([#3200](https://github.com/snapcore/snapcraft/pull/3200))
-   extensions: introduce flutter-dev [@sergiusens](https://github.com/sergiusens) ([#3199](https://github.com/snapcore/snapcraft/pull/3199))
-   extensions: introduce flutter-master [@sergiusens](https://github.com/sergiusens) ([#3195](https://github.com/snapcore/snapcraft/pull/3195))
-   riscv64 support [@xnox](https://github.com/xnox) ([#3186](https://github.com/snapcore/snapcraft/pull/3186))
-   plugins: add support for local v2 plugins (core20) [@cjp256](https://github.com/cjp256) ([#3118](https://github.com/snapcore/snapcraft/pull/3118))
-   snap: support for lzo as a compression target [@sergiusens](https://github.com/sergiusens) ([#3189](https://github.com/snapcore/snapcraft/pull/3189))

Maintenance
-----------

-   pyinstaller: workaround pkg_resources issue [@sergiusens](https://github.com/sergiusens) ([#3201](https://github.com/snapcore/snapcraft/pull/3201))
-   extensions: export content snap egl vendor dir [@sergiusens](https://github.com/sergiusens) ([#3190](https://github.com/snapcore/snapcraft/pull/3190))
-   cli: use snap pack instead of mksquashfs [@sergiusens](https://github.com/sergiusens) ([#3173](https://github.com/snapcore/snapcraft/pull/3173))
-   extensions: plug the opengl interface for GNOME [@sergiusens](https://github.com/sergiusens) ([#3193](https://github.com/snapcore/snapcraft/pull/3193))

Bug Fixes
---------

-   link_or_copy: do not try to create hardlinks to symlinks. [@hpoul](https://github.com/hpoul) ([#3174](https://github.com/snapcore/snapcraft/pull/3174))
-   cli: allow promoting from edge without --yes [@sergiusens](https://github.com/sergiusens) ([#3185](https://github.com/snapcore/snapcraft/pull/3185))
-   maven plugin: improve error message when target libs are not found. [@edumucelli](https://github.com/edumucelli) ([#3179](https://github.com/snapcore/snapcraft/pull/3179))
-   cli: unset false boolean flags in environment [@cjp256](https://github.com/cjp256) ([#3196](https://github.com/snapcore/snapcraft/pull/3196))
-   cli: use maxval of UnknownLength for pack progress [@sergiusens](https://github.com/sergiusens) ([#3187](https://github.com/snapcore/snapcraft/pull/3187))
-   build providers: check revision before switching [@sergiusens](https://github.com/sergiusens) ([#3184](https://github.com/snapcore/snapcraft/pull/3184))

Specifications and Documentation
--------------------------------

-   extensions: introduce flutter-master [@sergiusens](https://github.com/sergiusens) ([#3195](https://github.com/snapcore/snapcraft/pull/3195))

Tooling
-------

-   tools: fix environment-setup to work on aarch64 [@cjp256](https://github.com/cjp256) ([#3176](https://github.com/snapcore/snapcraft/pull/3176))

[/details]