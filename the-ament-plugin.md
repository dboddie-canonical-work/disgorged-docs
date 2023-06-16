.. 8643.md

.. _the-ament-plugin:

# The ament plugin

The `ament` plugin is useful when building [ROS2](https://index.ros.org/doc/ros2/) parts.

> ⓘ This plugin is only available to _core_ and _core18_ based snaps. See [Base snaps](/t/base-snaps/11198) for details.

This plugin uses the common plugin keywords as well as those for "sources". For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).

Additionally, this plugin uses the following plugin-specific keywords:

- **`version`** (string)
     The ROS2 version required by this system. This relates to the ros2 tags.
      Defaults to `release-beta3`.

For examples, search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+ament%22&type=Code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.