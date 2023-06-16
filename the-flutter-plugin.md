.. 18746.md

.. _the-flutter-plugin:

# The flutter plugin

This `flutter` plugin is useful for building [Flutter](https://flutter.dev/) based parts.  This plugin uses the common plugin keywords as well as those for [sources](/t/snapcraft-parts-metadata/8336#heading--source). For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).

Plugin-specific features and syntax are dependent on which [base](/t/base-snaps/11198) is being used, as outlined below:

- [base: core22](#heading--core22)
- [base: core18](#heading--core18)

See [Flutter applications](/t/flutter-applications/18768) for a simple example, or search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+flutter%22&type=Code) for projects using the plugin.

Further examples can also be found in the [Ubuntu Flutter Community](https://github.com/ubuntu-flutter-community/) on GitHub.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.

<h3 id='heading--core22'>base: core22</h3>

- **`flutter-channel`** (enum: [stable, master, beta], default: _stable_)</br>
        The default flutter channel to use for the build.
- **`flutter-target`**  (string, default: _lib/main.dart_)</br>
          The flutter target to build.

Requires Snapcraft version  _7.3+_.

<h3 id='heading--core18'>base: core18</h3>
This plugin uses the following plugin-specific keywords:

- **`flutter-revision`** (string)</br>
      Defines which Flutter revision to use for the build. This must be a valid revision from the [Flutter repository](https://github.com/flutter/flutter).
- **`flutter-target`**   (string, default:  _lib/main.dart_)</br>
      The main entry-point file of the application.

Requires Snapcraft version  _4.1.1+_.