.. 8396.md

.. _deprecation-notices:

# Deprecation notices

This document contains a list of *snapcraft* deprecation notices and recommendations:

- [DN1](/t/deprecation-notice-1/8397): The `snap` keyword has been replaced by `prime`
- [DN2](/t/deprecation-notice-2/8398): Custom plugins should now be placed in `snap/plugins`
- [DN3](/t/deprecation-notice-3/8403): Assets in `setup/gui` should now be placed in `snap/gui`
- [DN4](/t/deprecation-notice-4/8404): The `history` command has been renamed to `list-revisions`
- [DN5](/t/deprecation-notice-5/8405): Aliases are now handled by the Snap Store, and shouldn't be placed in the snap
- [DN6](/t/deprecation-notice-6/8406): Use of the `snap` command with a directory has been deprecated in favour of the `pack` command
- [DN7](/t/deprecation-notice-7/8407): The `prepare` keyword has been replaced by `override-build` (or [`override-pull`](/t/scriptlets/4892))
- [DN8](/t/deprecation-notice-8/8408): The `build` keyword has been replaced by `override-build`
- [DN9](/t/deprecation-notice-9/8409): The `install` keyword has been replaced by `override-build`
- [DN10](/t/deprecation-notice-10/12463): The `version-script` keyword has been replaced by `snapcraftctl set-version`
- [DN11](/t/deprecation-notice-11/18046): The `push` keywords have been replaced by `upload` equivalents
- [DN12](/t/deprecation-notice-12/18047): The `registered` and `list-registered` keywords has been replaced by `list`
- [DN13](/t/deprecation-notice-13/23774): Support for legacy `core` projects will be removed in Snapcraft 5.0 (expected July 22, 2021)