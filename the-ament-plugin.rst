.. 8643.md

.. \_the-ament-plugin:

The ament plugin
================

The ``ament`` plugin is useful when building `ROS2 <https://index.ros.org/doc/ros2/>`__ parts.

   ⓘ This plugin is only available to *core* and *core18* based snaps. See `Base snaps <base-snaps.md>`__ for details.

This plugin uses the common plugin keywords as well as those for “sources”. For more information, see `Snapcraft parts metadata <snapcraft-parts-metadata.md>`__.

Additionally, this plugin uses the following plugin-specific keywords:

-  **``version``** (string) The ROS2 version required by this system. This relates to the ros2 tags. Defaults to ``release-beta3``.

For examples, search `GitHub <https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+ament%22&type=Code>`__ for projects already using the plugin.

   ⓘ This is a *snapcraft* plugin. See `Snapcraft plugins <snapcraft-plugins.md>`__ and `Supported plugins <supported-plugins.md>`__ for further details on how plugins are used.
