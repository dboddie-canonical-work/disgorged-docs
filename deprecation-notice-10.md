.. 12463.md

.. _deprecation-notice-10:

# Deprecation notice: 10

**The 'version-script' keyword has been replaced by `snapcraftctl set-version'**

_introduced in snapcraft 2.41_

The `version-script` keyword could be used to define a command to run from the working directory of the source tree root that printed a version string to the standard output.

This functionality has been replaced by the `snapcraftctl set-version` part scriptlet.

For more details, see [Part scriptlets](/t/using-external-metadata/4642#meta-scriptlet).

See [Deprecation notices](/t/deprecation-notices/8396)  for further announcements.