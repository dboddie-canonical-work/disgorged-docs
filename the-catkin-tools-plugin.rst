.. 8645.md

.. \_the-catkin-tools-plugin:

The catkin-tools plugin
=======================

The ``catkin_tools`` build plugin is useful when building `ROS <http://www.ros.org/>`__ parts.

This plugin depends on the `catkin <the-catkin-plugin.md>`__ plugin. The catkin plugin runs the configuration process that allows *catkin_tools* to run.

This plugin uses the same keywords and configurations as the *catkin* plugin. The difference is the installation of *catkin_tools* and, consequently, using *catkin_tools* to build.

For examples, search `GitHub <https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+catkin-tools%22&type=Code>`__ for projects already using the plugin.

Plugin-specific features and syntax are dependent on which `base <base-snaps.md>`__ is being used, as outlined below:

-  `base: core20 <#the-catkin-tools-plugin-heading--core20>`__
-  `base: core18 \| core <#the-catkin-tools-plugin-heading--core18>`__

This plugin uses the common plugin keywords as well as those for “sources”. For more information, see `Snapcraft parts metadata <snapcraft-parts-metadata.md>`__.

##

.. raw:: html

   <h3 id="the-catkin-tools-plugin-heading--core20">

base: core20

.. raw:: html

   </h3>

For core20, this plugin is designed to work with the `ROS 1 Noetic Extension <the-ros-1-noetic-extension.md>`__. If not using this extension, it is required to set the ``ROS_DISTRO`` environment variable to ``noetic`` using ``build-environment``.

This plugin enables the following plugin-specific keywords on core20:

-  **``catkin-tools-packages``** (list of strings) List of catkin packages to build. If not specified, all packages in the workspace will be built. If set to an empty list (``[]``), no packages will be built, which could be useful if you only want ROS debs in the snap.

-  **``catkin-tools-cmake-args``** (list of strings) Arguments to pass to cmake projects.

##

.. raw:: html

   <h3 id="the-catkin-tools-plugin-heading--core18">

base: core|core18

.. raw:: html

   </h3>

This plugin enables core|core18 properties of the `catkin plugin </t/the-catkin-plugin/8644#the-catkin-tools-plugin-heading--core18>`__.
