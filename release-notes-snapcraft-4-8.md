.. 24944.md

.. _release-notes-snapcraft-4-8:

# Release notes: Snapcraft 4.8

The principle focus for Snapcraft 4.8 has been the removal of the experimental flag from [package repositories](/t/snapcraft-package-repositories/15475), which has been completed.

For general details, including installation instructions, see [Snapcraft overview](https://snapcraft.io/docs/snapcraft-overview), or take a look at [Snapcraft release notes](https://snapcraft.io/docs/snapcraft-release-notes) for other *Snapcraft* releases.

## Package repositories

This feature is finally stable and is documented at [Snapcraft package repositories](/t/snapcraft-package-repositories/15475).

* [PR #3520](https://github.com/snapcore/snapcraft/pull/3520)

## Bug fixes

### apt cache: improve error handling when packages do not have candidates available

* [LP: #1853682](https://bugs.launchpad.net/snapcraft/+bug/1853682)
* [PR #3528](https://github.com/snapcore/snapcraft/pull/3528)

### project: validate snapcraft yaml before using it

* [LP: #1853682](https://bugs.launchpad.net/snapcraft/+bug/1853682)
* [PR: #3526](https://github.com/snapcore/snapcraft/pull/3526)

### ua manager: install ubuntu-advantage-tools as needed

* [PR: #3524](https://github.com/snapcore/snapcraft/pull/3524)

### build providers: set hostname for lxd

* [PR: #3521](https://github.com/snapcore/snapcraft/pull/3521)

### dotnet plugin: use https for release metadata url

* [PR: #3525](https://github.com/snapcore/snapcraft/pull/3525)