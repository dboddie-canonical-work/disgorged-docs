.. 8616.md

.. _the-autotools-plugin:

# The autotools plugin

The `autotools` plugin is useful for [Automake/Autotools](https://www.gnu.org/software/automake/) based parts.

Autotools-based projects are easy to recognise, as they're typically built and installed with the following commands: `./configure && make && make install`.

This plugin uses the common plugin keywords as well as those for [sources](/t/snapcraft-parts-metadata/8336#heading--source). For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).

Additional features and syntax are dependent on which [base](/t/base-snaps/11198) is being used, as outlined below:

- [base: core22](#heading--core22)
- [base: core20](#heading--core20)
- [base: core18 | core](#heading--core18)

See [C/C++ applications](/t/c-c-applications/7817) for a simple example, or search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+autotools%22&type=Code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.

<h3 id='heading--core22'>base: core22</h3>

1. the *autotools* plugin first attempts to build the project using `./configure`
2. if the *configure* script does not yet exist, it will attempt to run `./autoconf --install`.

- **`autotools-configure-parameters`** (list of strings)
     Configure flags to pass to the build such as those shown by running `./configure --help`

Requires Snapcraft version _7.0+_.

<h3 id='heading--core20'>base: core20</h3>

1. the *autotools* plugin first attempts to build the project using `./configure`
1. if the *configure* script does not yet exist, it will attempt to run `./autoconf --install`.

In addition, this plugin uses the following plugin-specific keywords:

- **`autotools-configure-parameters`** (previously _configflags_) (list of strings)
     Configure flags to pass to the build such as those shown by running `./configure --help`

Requires Snapcraft version _4.0+_.

<h3 id='heading--core18'>base: core18 | core</h3>

1. the *autotools* plugin first attempts to build the project using `./configure`.
1. if the *configure* script does not yet exist, it will attempt to run `./autogen`.
1. if *autogen* doesn't exist, the plugin will run `autoreconf`.

In addition, this plugin uses the following plugin-specific keywords:

- **`configflags`** (list of strings)
     Configure flags to pass to the build such as those shown by running `./configure --help`
- **`install-via`** (enum, 'destdir' or 'prefix')
     Whether to install via DESTDIR or by using --prefix (default is
      'destdir')

Requires Snapcraft version _3.x_.