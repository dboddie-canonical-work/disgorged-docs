.. 4282.md

.. _the-maven-plugin:

# The maven plugin

This plugin is useful for building parts that use maven.

The maven build system is commonly used to build Java projects. The plugin requires a pom.xml in the root of the source tree.

This plugin is only available to *core22* and *core18* based snaps. See [Base snaps](https://forum.snapcraft.io/t/base-snaps/11198) for details.

<h3 id='heading--core22'>base: core22 and base: core18</h3>

This plugin uses the following plugin-specific keywords:

- **`maven-options`**:
  An array of maven command line options.

  Example:

  ```yaml
   YourJavaApp:
    plugin: maven
    source: https://github.com/apache/tomcat.git
    source-tag: TOMCAT_9_0_5
    source_tag: trunk
    source-type: git
    maven-options:
      [-DskipTests=true, -Dsomarg=false]
  ```

For examples, search [GitHub](https://github.com/search?q=path%3A**%2Fsnapcraft.yaml+gopath&type=code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.