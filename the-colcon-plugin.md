.. 11895.md

.. _the-colcon-plugin:

# The colcon plugin

The `colcon` plugin is useful when building [ROS 2](http://www.ros.org/) parts that use [colcon](https://colcon.readthedocs.io/en/released/).

Plugin-specific features and syntax are dependent on which [base](/t/base-snaps/11198) is being used, as outlined below:

- [base: core22](#heading--core22)
- [base: core20](#heading--core20)
- [base: core18 | core](#heading--core18)

This plugin uses the common plugin keywords as well as those for "sources". For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).

## <h3 id='heading--core22'>base: core22</h3>

For core22, this plugin is designed to work with the [ROS 2 Humble extension](/t/the-ros-2-humble-extension/30809).  If not using this extension, it is required to set the `ROS_DISTRO` environment variable to `humble` using `build-environment`.

This plugin enables the following plugin-specific keywords on core22:

- **`colcon-ament-cmake-args`** (list of strings)
Arguments to pass to *ament_cmake* packages. Note that any arguments here that
match colcon arguments need to be prefixed with a space. This can be done by
quoting each argument with a leading space.
- **`colcon-catkin-cmake-args`** (list of strings)
Arguments to pass to catkin packages. Note that any arguments here which match
colcon arguments need to be prefixed with a space. This can be done by quoting
each argument with a leading space.
- **`colcon-cmake-args`** (list of strings)
Arguments to pass to cmake projects. Note that any arguments here which match
colcon arguments need to be prefixed with a space. This can be done by quoting
each argument with a leading space.
- **`colcon-packages`** (list of strings)
List of colcon packages to build. If not specified, all packages in the
workspace will be built. If set to an empty list (`[]`), no packages will
be built, which could be useful if you only want ROS debs in the snap.
- **`colcon-packages-ignore`** (list of strings)
List of packages for colcon to ignore.

## <h3 id='heading--core20'>base: core20</h3>

For core20, this plugin is designed to work with the [ROS 2 Foxy extension](/t/the-ros2-foxy-extension/19639).  If not using this extension, it is required to set the `ROS_DISTRO` environment variable to `foxy` using `build-environment`.

This plugin enables the following plugin-specific keywords on core20:

- **`colcon-ament-cmake-args`** (list of strings)
Arguments to pass to *ament_cmake* packages. Note that any arguments here that
match colcon arguments need to be prefixed with a space. This can be done by
quoting each argument with a leading space.
- **`colcon-catkin-cmake-args`** (list of strings)
Arguments to pass to catkin packages. Note that any arguments here which match
colcon arguments need to be prefixed with a space. This can be done by quoting
each argument with a leading space.
- **`colcon-cmake-args`** (list of strings)
Arguments to pass to cmake projects. Note that any arguments here which match
colcon arguments need to be prefixed with a space. This can be done by quoting
each argument with a leading space.
- **`colcon-packages`** (list of strings)
List of colcon packages to build. If not specified, all packages in the
workspace will be built. If set to an empty list (`[]`), no packages will
be built, which could be useful if you only want ROS debs in the snap.
- **`colcon-packages-ignore`** (list of strings)
List of packages for colcon to ignore.

## <h3 id='heading--core18'>base: core18</h3>

This plugin enables the following plugin-specific keywords on core18:

- **`colcon-packages`** (list of strings)
List of colcon packages to build. If not specified, all packages in the
workspace will be built. If set to an empty list (`[]`), no packages will
be built, which could be useful if you only want ROS debs in the snap.
- **`colcon-source-space`** (string)
The source space containing colcon packages (defaults to `src`).
- **`colcon-rosdistro`** (string)
The ROS distro to use. Available options are bouncy and crystal (defaults to
crystal), both of which are only compatible with core18 as the base.
- **`colcon-cmake-args`** (list of strings)
Arguments to pass to cmake projects. Note that any arguments here which match
colcon arguments need to be prefixed with a space. This can be done by quoting
each argument with a leading space.
- **`colcon-catkin-cmake-args`** (list of strings)
Arguments to pass to catkin packages. Note that any arguments here which match
colcon arguments need to be prefixed with a space. This can be done by quoting
each argument with a leading space.
- **`colcon-ament-cmake-args`** (list of strings)
Arguments to pass to ament_cmake packages. Note that any arguments here which
match colcon arguments need to be prefixed with a space. This can be done by
quoting each argument with a leading space.


# Related Information

See the [catkin plugin](/t/the-catkin-plugin/8644) for building ROS 1 parts.

For a simple example, see [ROS 2 applications](/t/ros2-applications/7823), or search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+colcon%22&type=Code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.