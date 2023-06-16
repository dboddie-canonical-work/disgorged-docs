.. 20810.md

.. _release-notes-snapcraft-4-4:

# Release notes: Snapcraft 4.4

The team behind Snapcraft is pleased to announce the release of [Snapcraft 4.4](https://github.com/snapcore/snapcraft/releases/tag/4.4).

Highlights for this release include:

* improved font generation performance when [desktop extensions](/t/supported-extensions/20521)
* updates to package repository definitions and behaviour
* metrics for [Progressive Releases](/t/progressive-releases/20913)
* many small but significant bug fixes

For general details, including installation instructions, see [Snapcraft overview](https://forum.snapcraft.io/t/snapcraft-overview/8940), or take a look at [Snapcraft release notes](https://forum.snapcraft.io/t/snapcraft-release-notes/10721) for other  *Snapcraft*  releases.

## New Features

### Command Line

Custom CA certificates can now be added to the build environments created by Snapcraft by using  `--add-ca-certificates`  with the [lifecycle](/t/parts-lifecycle/12231) related commands.

### Extensions

This release includes a new mechanism to pre-generate font caches with [desktop-related extensions](/t/supported-extensions/20521). This enables system font cache generation at install time, isolated from the potentially (ABI) incompatible host-generated cache.

To benefit from this feature, extension snaps will need to be rebuilt. More details about this feature can be found in the [specification](https://github.com/snapcore/snapcraft/blob/master/specifications/desktop-extensions-font-hook.org).

### Package repositories

The  *experimental*  [package repositories](/t/snapcraft-package-repositories/15475) has the following changes:

* the undocumented `$SNAPCRAFT_APT` variables have been removed.
* improved error handling and schema validation.

Additionally, the package repository [specification](https://github.com/snapcore/snapcraft/blob/master/specifications/package-repositories.org) has been finalised, hopefully opening a path to remove the _experimental_ flag for this feature.

### Updates to the Store

#### Progressive Releases

Metrics have been added to our progressive releases feature, as defined by the [specification](https://github.com/snapcore/snapcraft/blob/master/specifications/progressive-releases.org). Input on this feature is welcome on the [forum](https://forum.snapcraft.io/new-topic?title=Progressive%20Releases%20Feedback&category=snapcraft).

See [Progressive releases](/t/progressive-releases/20913) for more details.

#### Snap Revisions

Snapcraft's  `revisions`  command is now internally using a new endpoint to provide much better results:

* table headers have changed to better represent architectures
* channels are now fully qualified (i.e.;  `<track/risk/branch>` )
* comma separated column entries no longer have a space separating each item

Refer to the [specification](https://github.com/snapcore/snapcraft/blob/master/specifications/history-to-releases.org) for further details.

## Full list of changes

The issues and features worked on for Snapcraft 4.4 are reflected in the following change list:

[details=List of changes for Snapcraft 4.4]
</br>
New Features
------------

-   cli: remove spaces from progressive metrics [@sergiusens](https://github.com/sergiusens) ([#3335](https://github.com/snapcore/snapcraft/pull/3335))
-   storeapi: add releases endpoint [@sergiusens](https://github.com/sergiusens) ([#3311](https://github.com/snapcore/snapcraft/pull/3311))
-   cli: provide option to install ca certs into build environment [@cjp256](https://github.com/cjp256) ([#3224](https://github.com/snapcore/snapcraft/pull/3224))
-   Add PYTHONPATH to environment (fixes #1893262) [@hellsworth](https://github.com/hellsworth) ([#3270](https://github.com/snapcore/snapcraft/pull/3270))
-   snap packaging: fetch remote icons configured via appstream [@cjp256](https://github.com/cjp256) ([#3241](https://github.com/snapcore/snapcraft/pull/3241))
-   pluginhandler: support using patchelf on strict snaps [@kyrofa](https://github.com/kyrofa) ([#3277](https://github.com/snapcore/snapcraft/pull/3277))
-   gnome extensions: multiarch bindtextdomain.so support [@galgalesh](https://github.com/galgalesh) ([#3127](https://github.com/snapcore/snapcraft/pull/3127))
-   db: introduce generalized datastore [@cjp256](https://github.com/cjp256) ([#3238](https://github.com/snapcore/snapcraft/pull/3238))
-   meta: write stubs for command-chain using hooks when needed [@sergiusens](https://github.com/sergiusens) ([#3296](https://github.com/snapcore/snapcraft/pull/3296))
-   cli: support snap --output [@cjp256](https://github.com/cjp256) ([#3297](https://github.com/snapcore/snapcraft/pull/3297))
-   extensions: configure hook for fonts [@sergiusens](https://github.com/sergiusens) ([#3299](https://github.com/snapcore/snapcraft/pull/3299))
-   storeapi: add support for reporting status of progressive releases [@maxiberta](https://github.com/maxiberta) ([#3306](https://github.com/snapcore/snapcraft/pull/3306))
-   package repositories: improve error handling [@cjp256](https://github.com/cjp256) ([#3334](https://github.com/snapcore/snapcraft/pull/3334))
-   spread tests: move package-repositories test snaps into own dir [@cjp256](https://github.com/cjp256) ([#3331](https://github.com/snapcore/snapcraft/pull/3331))

Maintenance
-----------

-   cli: update revisions to use releases API [@sergiusens](https://github.com/sergiusens) ([#3329](https://github.com/snapcore/snapcraft/pull/3329))
-   storeapi: remove bindings for history [@sergiusens](https://github.com/sergiusens) ([#3332](https://github.com/snapcore/snapcraft/pull/3332))
-   v1 plugins: lock godep's dependencies [@cjp256](https://github.com/cjp256) ([#3285](https://github.com/snapcore/snapcraft/pull/3285))
-   readme: remove link to Google+ [@timsueberkrueb](https://github.com/timsueberkrueb) ([#3292](https://github.com/snapcore/snapcraft/pull/3292))
-   storeapi: drop arch requirement for get_channel_mapping() [@cjp256](https://github.com/cjp256) ([#3301](https://github.com/snapcore/snapcraft/pull/3301))
-   build(deps-dev): bump junit from 3.8.1 to 4.13.1 in /tests/spread/plugins/v1/maven/snaps/legacy-maven-hello/my-app [@dependabot](https://github.com/dependabot) ([#3316](https://github.com/snapcore/snapcraft/pull/3316))
-   build(deps-dev): bump junit from 3.8.1 to 4.13.1 in /tests/spread/plugins/v1/maven/snaps/maven-hello/my-app [@dependabot](https://github.com/dependabot) ([#3315](https://github.com/snapcore/snapcraft/pull/3315))
-   spread tests: introduce electron-builder test [@cjp256](https://github.com/cjp256) ([#3312](https://github.com/snapcore/snapcraft/pull/3312))
-   unit tests: fix runtests.sh not filtering tests when passed a subdirectory [@maxiberta](https://github.com/maxiberta) ([#3305](https://github.com/snapcore/snapcraft/pull/3305))
-   electron-builder spread test: sync expected snapcraft.yaml [@cjp256](https://github.com/cjp256) ([#3323](https://github.com/snapcore/snapcraft/pull/3323))
-   package repositories: drop $SNAPCRAFT_APT_HOST_ARCH variable [@cjp256](https://github.com/cjp256) ([#3322](https://github.com/snapcore/snapcraft/pull/3322))
-   package repositories: drop $SNAPCRAFT_APT_RELEASE variable [@cjp256](https://github.com/cjp256) ([#3328](https://github.com/snapcore/snapcraft/pull/3328))
-   flutter tests: updated for latest embedder [@kenvandine](https://github.com/kenvandine) ([#3310](https://github.com/snapcore/snapcraft/pull/3310))
-   lxd unit tests: simplify command checking pattern [@cjp256](https://github.com/cjp256) ([#3326](https://github.com/snapcore/snapcraft/pull/3326))

Bug Fixes
---------

-   package repositories: fix case where formats is empty [@cjp256](https://github.com/cjp256) ([#3330](https://github.com/snapcore/snapcraft/pull/3330))
-   meta: add error check for "command not found" [@cjp256](https://github.com/cjp256) ([#3321](https://github.com/snapcore/snapcraft/pull/3321))
-   snapcraftctl: add checks for empty string for set-version & set-grade [@cjp256](https://github.com/cjp256) ([#3325](https://github.com/snapcore/snapcraft/pull/3325))
-   pluginhandler: properly handle snapcraftctl errors [@cjp256](https://github.com/cjp256) ([#3317](https://github.com/snapcore/snapcraft/pull/3317))
-   schema: add regex to validate description is non-empty [@cjp256](https://github.com/cjp256) ([#3303](https://github.com/snapcore/snapcraft/pull/3303))
-   set ROS_PYTHON_VERSION for rosdep [@artivis](https://github.com/artivis) ([#3324](https://github.com/snapcore/snapcraft/pull/3324))
-   Set ROS_VERSION for rosdep in plugins v1 [@artivis](https://github.com/artivis) ([#3313](https://github.com/snapcore/snapcraft/pull/3313))
-   repo: install requested build-package versions [@cjp256](https://github.com/cjp256) ([#3221](https://github.com/snapcore/snapcraft/pull/3221))
-   project loader: install dirmngr prior to configuring package repositories [@cjp256](https://github.com/cjp256) ([#3294](https://github.com/snapcore/snapcraft/pull/3294))
-   build providers: fix issues running on Windows [@sergiusens](https://github.com/sergiusens) ([#3289](https://github.com/snapcore/snapcraft/pull/3289))
-   cmake v2 plugin: add help for cmake generators [@sergiusens](https://github.com/sergiusens) ([#3288](https://github.com/snapcore/snapcraft/pull/3288))
-   setup.py: assert with helpful error when unable to determine version [@cjp256](https://github.com/cjp256) ([#3307](https://github.com/snapcore/snapcraft/pull/3307))

Specifications and Documentation
--------------------------------

-   specifications: v1 history to v2 releases [@sergiusens](https://github.com/sergiusens) ([#3304](https://github.com/snapcore/snapcraft/pull/3304))
-   specification: desktop extension font hook [@sergiusens](https://github.com/sergiusens) ([#3295](https://github.com/snapcore/snapcraft/pull/3295))
-   specifications: finalization of package repositories spec [@cjp256](https://github.com/cjp256) ([#3333](https://github.com/snapcore/snapcraft/pull/3333))
[/details]