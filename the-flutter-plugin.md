.. 18746.md

.. _the-flutter-plugin:

# The flutter plugin

This `flutter` plugin is useful for building [Flutter](https://flutter.dev/) based parts.  This plugin uses the common plugin keywords as well as those for [sources](snapcraft-parts-metadata.md#the-flutter-plugin-heading--source). For more information, see [Snapcraft parts metadata](snapcraft-parts-metadata.md).

Plugin-specific features and syntax are dependent on which [base](base-snaps.md) is being used, as outlined below:

- [base: core22](#the-flutter-plugin-heading--core22)
- [base: core18](#the-flutter-plugin-heading--core18)

See [Flutter applications](flutter-applications.md) for a simple example, or search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+flutter%22&type=Code) for projects using the plugin.

Further examples can also be found in the [Ubuntu Flutter Community](https://github.com/ubuntu-flutter-community/) on GitHub.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](snapcraft-plugins.md) and [Supported plugins](supported-plugins.md) for further details on how plugins are used.

<h3 id='the-flutter-plugin-heading--core22'>base: core22</h3>

- **`flutter-channel`** (enum: [stable, master, beta], default: _stable_)</br>
        The default flutter channel to use for the build.
- **`flutter-target`**  (string, default: _lib/main.dart_)</br>
          The flutter target to build.

Requires Snapcraft version  _7.3+_.

<h3 id='the-flutter-plugin-heading--core18'>base: core18</h3>
This plugin uses the following plugin-specific keywords:

- **`flutter-revision`** (string)</br>
      Defines which Flutter revision to use for the build. This must be a valid revision from the [Flutter repository](https://github.com/flutter/flutter).
- **`flutter-target`**   (string, default:  _lib/main.dart_)</br>
      The main entry-point file of the application.

Requires Snapcraft version  _4.1.1+_.