.. 8623.md

.. _the-meson-plugin:

# The meson plugin

The `meson` plugin is useful for building [Meson](https://mesonbuild.com/)-based parts.

Projects using the Meson build system will contain a _meson.build_ file that drives the build, and the plugin runs the following commands to build your project:

1. `meson`
2. `ninja`
3. `ninja install`

This plugin uses the common plugin keywords as well as those for [sources](/t/snapcraft-parts-metadata/8336#heading--source). For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).

For examples, search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+meson%22&type=Code) for projects using the plugin.

Plugin-specific features and syntax are dependent on which [base](/t/base-snaps/11198) is being used, as outlined below:

- [base: core22](#heading--core22)
- [base: core20](#heading--core20)
- [base: core18 | core](#heading--core18)

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.

<h3 id='heading--core22'>base: core22</h3>

This plugin uses the following plugin-specific keywords:

- **`meson-parameters`** (list of strings)
     List of parameters to pass to the _meson_ command.

Requires Snapcraft version _7.0+_.

<h3 id='heading--core20'>base: core20</h3>

This plugin uses the following plugin-specific keywords:

- **`meson-parameters`** (list of strings)
     List of parameters to pass to the _meson_ command.

- **`meson-version`** (string)
     Version of _meson_ to download from [PyPI](https://pypi.org/project/meson/) (e.g. 0.62.1).


Requires Snapcraft version _4.0+_.

<h3 id='heading--core18'>base: core18 | core</h3>

This plugin uses the following plugin-specific keywords:


- **`meson-parameters`** (list of strings)
     List of parameters to pass to the _meson_ command.

- **`meson-version`** (string)
     Version of _meson_ to download from [PyPI](https://pypi.org/project/meson/) (e.g. 0.62.1).