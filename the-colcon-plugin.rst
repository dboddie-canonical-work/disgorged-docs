.. 11895.md

.. \_the-colcon-plugin:

The colcon plugin
=================

The ``colcon`` plugin is useful when building `ROS 2 <http://www.ros.org/>`__ parts that use `colcon <https://colcon.readthedocs.io/en/released/>`__.

Plugin-specific features and syntax are dependent on which `base <base-snaps.md>`__ is being used, as outlined below:

-  `base: core22 <#the-colcon-plugin-heading--core22>`__
-  `base: core20 <#the-colcon-plugin-heading--core20>`__
-  `base: core18 \| core <#the-colcon-plugin-heading--core18>`__

This plugin uses the common plugin keywords as well as those for “sources”. For more information, see `Snapcraft parts metadata <snapcraft-parts-metadata.md>`__.

##

.. raw:: html

   <h3 id="the-colcon-plugin-heading--core22">

base: core22

.. raw:: html

   </h3>

For core22, this plugin is designed to work with the `ROS 2 Humble extension <the-ros-2-humble-extension.md>`__. If not using this extension, it is required to set the ``ROS_DISTRO`` environment variable to ``humble`` using ``build-environment``.

This plugin enables the following plugin-specific keywords on core22:

-  **``colcon-ament-cmake-args``** (list of strings) Arguments to pass to *ament_cmake* packages. Note that any arguments here that match colcon arguments need to be prefixed with a space. This can be done by quoting each argument with a leading space.
-  **``colcon-catkin-cmake-args``** (list of strings) Arguments to pass to catkin packages. Note that any arguments here which match colcon arguments need to be prefixed with a space. This can be done by quoting each argument with a leading space.
-  **``colcon-cmake-args``** (list of strings) Arguments to pass to cmake projects. Note that any arguments here which match colcon arguments need to be prefixed with a space. This can be done by quoting each argument with a leading space.
-  **``colcon-packages``** (list of strings) List of colcon packages to build. If not specified, all packages in the workspace will be built. If set to an empty list (``[]``), no packages will be built, which could be useful if you only want ROS debs in the snap.
-  **``colcon-packages-ignore``** (list of strings) List of packages for colcon to ignore.

##

.. raw:: html

   <h3 id="the-colcon-plugin-heading--core20">

base: core20

.. raw:: html

   </h3>

For core20, this plugin is designed to work with the `ROS 2 Foxy extension <the-ros2-foxy-extension.md>`__. If not using this extension, it is required to set the ``ROS_DISTRO`` environment variable to ``foxy`` using ``build-environment``.

This plugin enables the following plugin-specific keywords on core20:

-  **``colcon-ament-cmake-args``** (list of strings) Arguments to pass to *ament_cmake* packages. Note that any arguments here that match colcon arguments need to be prefixed with a space. This can be done by quoting each argument with a leading space.
-  **``colcon-catkin-cmake-args``** (list of strings) Arguments to pass to catkin packages. Note that any arguments here which match colcon arguments need to be prefixed with a space. This can be done by quoting each argument with a leading space.
-  **``colcon-cmake-args``** (list of strings) Arguments to pass to cmake projects. Note that any arguments here which match colcon arguments need to be prefixed with a space. This can be done by quoting each argument with a leading space.
-  **``colcon-packages``** (list of strings) List of colcon packages to build. If not specified, all packages in the workspace will be built. If set to an empty list (``[]``), no packages will be built, which could be useful if you only want ROS debs in the snap.
-  **``colcon-packages-ignore``** (list of strings) List of packages for colcon to ignore.

##

.. raw:: html

   <h3 id="the-colcon-plugin-heading--core18">

base: core18

.. raw:: html

   </h3>

This plugin enables the following plugin-specific keywords on core18:

-  **``colcon-packages``** (list of strings) List of colcon packages to build. If not specified, all packages in the workspace will be built. If set to an empty list (``[]``), no packages will be built, which could be useful if you only want ROS debs in the snap.
-  **``colcon-source-space``** (string) The source space containing colcon packages (defaults to ``src``).
-  **``colcon-rosdistro``** (string) The ROS distro to use. Available options are bouncy and crystal (defaults to crystal), both of which are only compatible with core18 as the base.
-  **``colcon-cmake-args``** (list of strings) Arguments to pass to cmake projects. Note that any arguments here which match colcon arguments need to be prefixed with a space. This can be done by quoting each argument with a leading space.
-  **``colcon-catkin-cmake-args``** (list of strings) Arguments to pass to catkin packages. Note that any arguments here which match colcon arguments need to be prefixed with a space. This can be done by quoting each argument with a leading space.
-  **``colcon-ament-cmake-args``** (list of strings) Arguments to pass to ament_cmake packages. Note that any arguments here which match colcon arguments need to be prefixed with a space. This can be done by quoting each argument with a leading space.

Related Information
===================

See the `catkin plugin <the-catkin-plugin.md>`__ for building ROS 1 parts.

For a simple example, see `ROS 2 applications <ros-2-deployment-with-snaps.md>`__, or search `GitHub <https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+colcon%22&type=Code>`__ for projects already using the plugin.

   ⓘ This is a *snapcraft* plugin. See `Snapcraft plugins <snapcraft-plugins.md>`__ and `Supported plugins <supported-plugins.md>`__ for further details on how plugins are used.