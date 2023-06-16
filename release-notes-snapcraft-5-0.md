.. 25751.md

.. _release-notes-snapcraft-5-0:

# Release notes: Snapcraft 5.0

Snapcraft 5.0 is a milestone release that marks the end of a significant development cycle while adding several new and important features, including:

- New _snapcraft metrics_ command
- Metadata links added to _snapcraft.yaml_
- Removal of legacy code base

For general details, including installation instructions, see [Snapcraft overview](https://snapcraft.io/docs/snapcraft-overview), or take a look at [Snapcraft release notes](https://snapcraft.io/docs/snapcraft-release-notes) for other *Snapcraft* releases.

## Snapcraft metrics

The `snapcraft metrics` command can be used to track installation and usage statistics for snaps published with your developer account.

For further details, see [Snapcraft metrics](/t/snapcraft-metrics/25732).

## Metadata links added to _snapcraft.yaml_

You can now add user-friendly bespoke links, such as a donation URL, a contact link, or for filing issues, to a snap's _snapcraft.yaml_.

These links are translated into a more _wire protocol_ friendly syntax for `snap.yaml` which can then be consumed by the Snap Store to enhance your snap's listing.

See [Snapcraft.yaml reference](/t/snapcraft-yaml-reference/4276) for further details.

## Removal of legacy code base

For a long time, since the creation of [base snaps](/t/base-snaps/11198), Snapcraft has maintained two code bases inside the same product - when no base was detected, Snapcraft would re-execute itself into the old code base.

The absence of a base in `snapcraft.yaml` triggered this behaviour for backwards compatibility, and this absence essentially meant building for an Ubuntu 16.04 target.

Ubuntu 16.04 is now in its ESM phase, and it's support has been dropped from Snapcraft 5+.  Publishers needing continued support for `base: core` can now use Snapcraft's 4.x track which maintains the old Ubuntu 16.04 compatible code base.

See [Snapcraft and Extended Security Maintenance](/t/snapcraft-and-extended-security-maintenance/24297) for more details.

## Full list of changes

Special thanks to the contributors that made this release happen: [@3v1n0](https://github.com/3v1n0), [@Blacksmoke16](https://github.com/Blacksmoke16), [@artivis](https://github.com/artivis), [@cjp256](https://github.com/cjp256), [@cmatsuoka](https://github.com/cmatsuoka), [@jriddell](https://github.com/jriddell), [@kyrofa](https://github.com/kyrofa) and [@sergiusens](https://github.com/sergiusens).

* storeapi: improve candid interaction errors (CRAFT-135) [@sergiusens](https://github.com/sergiusens) ([#3562](https://github.com/snapcore/snapcraft/pull/3562))
* spread tests: store metrics against staging (CRAFT-391) [@sergiusens](https://github.com/sergiusens) ([#3561](https://github.com/snapcore/snapcraft/pull/3561))
* cli: introduce metrics command (CRAFT-387) [@cjp256](https://github.com/cjp256) ([#3560](https://github.com/snapcore/snapcraft/pull/3560))
* store: add API support for metrics (CRAFT-386) [@cjp256](https://github.com/cjp256) ([#3559](https://github.com/snapcore/snapcraft/pull/3559))
* storeapi: introduce data model module for metrics (CRAFT-385) [@cjp256](https://github.com/cjp256) ([#3558](https://github.com/snapcore/snapcraft/pull/3558))
* Update Crystal v1 plugin [@Blacksmoke16](https://github.com/Blacksmoke16) ([#3541](https://github.com/snapcore/snapcraft/pull/3541))
* store: Add ReviewQueued status [@3v1n0](https://github.com/3v1n0) ([#3556](https://github.com/snapcore/snapcraft/pull/3556))
* cli: introduce echo.echo_with_pager_if_needed() (CRAFT-380) [@cjp256](https://github.com/cjp256) ([#3557](https://github.com/snapcore/snapcraft/pull/3557))
* cli: add support for parallel remote builds [@kyrofa](https://github.com/kyrofa) ([#3554](https://github.com/snapcore/snapcraft/pull/3554))
* project: validate metadata links (CRAFT-369) [@sergiusens](https://github.com/sergiusens) ([#3555](https://github.com/snapcore/snapcraft/pull/3555))
* cli: make remote-build more user-friendly [@kyrofa](https://github.com/kyrofa) ([#3553](https://github.com/snapcore/snapcraft/pull/3553))
* dependencies: update click to 8.0.1 [@kyrofa](https://github.com/kyrofa) ([#3551](https://github.com/snapcore/snapcraft/pull/3551))
* meta: support for metadata links (CRAFT-370) [@sergiusens](https://github.com/sergiusens) ([#3552](https://github.com/snapcore/snapcraft/pull/3552))
* update kde neon extension to use the newer content snap with qt-5-15-3 [@jriddell](https://github.com/jriddell) ([#3547](https://github.com/snapcore/snapcraft/pull/3547))
* storeapi: log responses and registration error code [@sergiusens](https://github.com/sergiusens) ([#3550](https://github.com/snapcore/snapcraft/pull/3550))
* repo: normalize only if there are packages to unpack [@cmatsuoka](https://github.com/cmatsuoka) ([#3534](https://github.com/snapcore/snapcraft/pull/3534))
* collaborators: remove feature [@sergiusens](https://github.com/sergiusens) ([#3548](https://github.com/snapcore/snapcraft/pull/3548))
* project: convert core warning to error [@sergiusens](https://github.com/sergiusens) ([#3546](https://github.com/snapcore/snapcraft/pull/3546))
* Core base removal [@sergiusens](https://github.com/sergiusens) ([#3544](https://github.com/snapcore/snapcraft/pull/3544))
* ROS plugins v2 misc fixes [@artivis](https://github.com/artivis) ([#3536](https://github.com/snapcore/snapcraft/pull/3536))
* snap: remove support for legacy re-exec (CRAFT-205) [@sergiusens](https://github.com/sergiusens) ([#3543](https://github.com/snapcore/snapcraft/pull/3543))
* spread tests: remove 16.04 and core (CRAFT-210) [@sergiusens](https://github.com/sergiusens) ([#3540](https://github.com/snapcore/snapcraft/pull/3540))