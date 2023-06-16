.. 8511.md

.. _the-gulp-plugin:

# The gulp plugin

The `gulp` plugin can be used with JavaScript projects using [gulp.js](https://gulpjs.com/), the streaming build system.

The plugin uses *gulp* to drive the build, and requires a `gulpfile.js` in the root of the source.

> ⓘ This plugin is only available to _core_ and _core18_ based snaps. See [Base snaps](/t/base-snaps/11198) for details.

This plugin uses the common plugin keywords as well as those for "sources". For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).

Additionally, this plugin uses the following plugin-specific keywords:

- **`gulp-tasks`** (list)
  A list of gulp tasks to run.
- **`node-engine`** (string)
  The version of *node.js* to use for the build.

For examples, search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+gulp%22&type=Code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.