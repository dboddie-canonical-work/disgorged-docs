.. 8644.md

.. _the-catkin-plugin:

# The catkin plugin

The `catkin` plugin is useful when building [ROS 1](http://www.ros.org/) parts.

Plugin-specific features and syntax are dependent on which [base](/t/base-snaps/11198) is being used, as outlined below:

- [base: core20](#heading--core20)
- [base: core18 | core](#heading--core18)

This plugin uses the common plugin keywords as well as those for "sources". For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).


## <h3 id='heading--core20'>base: core20</h3>

For core20, this plugin is designed to work with the [ROS 1 Noetic extension](/t/the-ros-1-noetic-extension/20070).  If not using this extension, it is required to set the `ROS_DISTRO` environment variable to `noetic` using `build-environment`.

This plugin enables the following plugin-specific keywords on core20:

Additionally, this plugin uses the following plugin-specific keywords:

- **`catkin-packages`** (list of strings)
List of catkin packages to build. If not specified, all packages in the
workspace will be built. If set to an empty list (`[]`), no packages will
be built, which could be useful if you only want ROS debs in the snap.

- **`catkin-packages-ignore`** (list of strings)
List of catkin packages to ignore (i.e. not build or install). If not specified or set to an empty list ([]), no packages will be ignored.

- **`catkin-cmake-args`** (list of strings)
Arguments to pass to cmake projects.

## <h3 id='heading--core18'>base: core | core18</h3>

For core, this plugin is designed to work with the ROS Kinetic distro.

For core18, this plugin is designed to work with the ROS Melodic distro.

This plugin enables the following plugin-specific keywords on core|core18:

- **`catkin-packages`** (list of strings)
List of catkin packages to build. If not specified, all packages in the
workspace will be built. If set to an empty list (`[]`), no packages will
be built.
- **`source-space`** (string)
The source space containing Catkin packages. By default this is `src`.
- **`include-roscore`** (boolean)
Whether or not to include roscore with the part. Defaults to true.
- **`rosinstall-files`** (list of strings)
List of rosinstall files to merge while pulling. Paths are relative to
the source.
- **`recursive-rosinstall`** (boolean)
Whether or not to recursively merge/update rosinstall files from fetched
sources. Will continue until all rosinstall files have been merged.
Defaults to false.
- **`catkin-cmake-args`** (list of strings)
Configure flags to pass onto the cmake invocation from catkin.
- **`underlay`** (object)
Used to inform Snapcraft that this snap isn't standalone, and is actually
overlaying a workspace from another snap via content sharing. Made up of
two properties:
    - **`build-path`** (string)
Build-time path to existing workspace to underlay the one being built,
for example `$SNAPCRAFT_STAGE/opt/ros/kinetic`.
    - **`run-path`** (string)
Run-time path of the underlay workspace (e.g. a subdirectory of the
content interface's 'target' attribute.)
- **`catkin-ros-master-uri`** (string)
The URI to ros master setting the env variable ROS_MASTER_URI. Defaults
to `http://localhost:11311`.

With core18, using the catkin plugin creates an external link that causes the security check of snapcraft to fail. This can be resolved by explicitly removing this link.
```
   stage:
     - -lib/systemd/system/sudo.service
```

See the [catkin-tools plugin](/t/the-catkin-tools-plugin/8645) plugin for additional methods for building ROS 1 parts. Also see the [colcon plugin](/t/the-colcon-plugin/11895) for building ROS 2 parts.

For a simple example, see [ROS applications](/t/ros-applications/7822), or search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+catkin%22&type=Code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.