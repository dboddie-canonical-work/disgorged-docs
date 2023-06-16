.. 4282.md

.. \_the-maven-plugin:

The maven plugin
================

This plugin is useful for building parts that use maven.

The maven build system is commonly used to build Java projects. The plugin requires a pom.xml in the root of the source tree.

This plugin is only available to *core22* and *core18* based snaps. See `Base snaps <base-snaps.md>`__ for details.

.. raw:: html

   <h3 id="the-maven-plugin-heading--core22">

base: core22 and base: core18

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keywords:

-  **``maven-options``**: An array of maven command line options.

   Example:

   .. code:: yaml

       YourJavaApp:
        plugin: maven
        source: https://github.com/apache/tomcat.git
        source-tag: TOMCAT_9_0_5
        source_tag: trunk
        source-type: git
        maven-options:
          [-DskipTests=true, -Dsomarg=false]

For examples, search `GitHub <https://github.com/search?q=path%3A**%2Fsnapcraft.yaml+gopath&type=code>`__ for projects already using the plugin.

   ⓘ This is a *snapcraft* plugin. See `Snapcraft plugins <snapcraft-plugins.md>`__ and `Supported plugins <supported-plugins.md>`__ for further details on how plugins are used.