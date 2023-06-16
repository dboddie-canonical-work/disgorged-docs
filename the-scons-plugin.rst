.. 8629.md

.. \_the-scons-plugin:

The scons plugin
================

The ``scons`` plugin is useful when building parts that use the `SCons <https://scons.org/>`__ construction tool.

   ⓘ This plugin is only available to *core* and *core18* based snaps. See `Base snaps <base-snaps.md>`__ for details.

Scons projects use a *SConstruct* file to drive the build.

This plugin uses the common plugin keywords as well as those for “sources”. For more information, see `Snapcraft parts metadata <snapcraft-parts-metadata.md>`__.

Additionally, this plugin uses the following plugin-specific keywords:

-  **``scons-options``** (list of strings) flags to pass to the build using the scons semantics for parameters.

For examples, search `GitHub <https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+scons%22&type=Code>`__ for projects already using the plugin.

   ⓘ This is a *snapcraft* plugin. See `Snapcraft plugins <snapcraft-plugins.md>`__ and `Supported plugins <supported-plugins.md>`__ for further details on how plugins are used.