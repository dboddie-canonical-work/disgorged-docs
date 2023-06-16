.. 8643.md

.. _the-ament-plugin:

# The ament plugin

The `ament` plugin is useful when building [ROS2](https://index.ros.org/doc/ros2/) parts.

> ⓘ This plugin is only available to _core_ and _core18_ based snaps. See [Base snaps](base-snaps.md) for details.

This plugin uses the common plugin keywords as well as those for "sources". For more information, see [Snapcraft parts metadata](snapcraft-parts-metadata.md).

Additionally, this plugin uses the following plugin-specific keywords:

- **`version`** (string)
     The ROS2 version required by this system. This relates to the ros2 tags.
      Defaults to `release-beta3`.

For examples, search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+ament%22&type=Code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](snapcraft-plugins.md) and [Supported plugins](supported-plugins.md) for further details on how plugins are used.