.. 8622.md

.. _the-make-plugin:

# The make plugin

The `make` plugin is useful when building [make](https://www.gnu.org/software/make/manual/make.html)-based parts. Make-based projects will typically include a *Makefile* that drives the build.

This plugin runs 'make' followed by 'make install', except when the `artifacts` keyword is used with _core18_ or _core_.

If your project uses [Automake](https://www.gnu.org/software/automake/), take a look at the [autotools](/t/the-autotools-plugin/8616) plugin. For examples, search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+make%22&type=Code) for projects using the plugin.

This plugin uses the common plugin keywords as well as those for "sources". For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).

Its features and syntax are dependent on which [base](/t/base-snaps/11198) is being used, as outlined below:

- [base: core22](#heading--core22)
- [base: core20](#heading--core20)
- [base: core18 | core](#heading--core18)

 > ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.

<h3 id='heading--core22'>base: core22</h3>


This plugin uses the following plugin-specific keywords:

- **`make-parameters`** (list of strings)
  Parameters to pass to the make command.

Use Snapcraft's [override-build](/t/snapcraft-parts-metadata/8336#heading--override-build) functionality to implement the equivalent `makefile`, `artifacts` and `make-install-var` functionality available to _core18_ and _core_ snaps.


Requires Snapcraft version _7.0+_.

<h3 id='heading--core20'>base: core20</h3>


This plugin uses the following plugin-specific keywords:

- **`make-parameters`** (list of strings)
  Parameters to pass to the make command.

Use Snapcraft's [override-build](/t/snapcraft-parts-metadata/8336#heading--override-build) functionality to implement the equivalent `makefile`, `artifacts` and `make-install-var` functionality available to _core18_ and _core_ snaps.

Requires Snapcraft version _4.0+_.

<h3 id='heading--core18'>base: core18 | core</h3>

This plugin uses the following plugin-specific keywords:

- **`artifacts`** (list)
  Link/copy the given files from the *make* output to the snap  installation directory. If specified, the `make install` step will be skipped.

- **`makefile`** (string)
  Use the given file as the *makefile*.

- **`make-parameters`** (list of strings)
  Parameters to pass to the make command.

- **`make-install-var`** (string; default: DESTDIR)
  Use this variable to redirect the installation into the snap.

Requires Snapcraft version _3.x_.