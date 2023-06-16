.. 8628.md

.. _the-qmake-plugin:

# The qmake plugin

The `qmake` plugin is useful when building [qmake](http://doc.qt.io/qt-5/qmake-manual.html)-based parts.

Qmake-based projects typically use [Qt](https://www.qt.io/), although not always, and are built using *.pro* files.

This plugin uses the common plugin keywords as well as those for [sources](/t/snapcraft-parts-metadata/8336#heading--source). For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).

Additional features and syntax are dependent on which [base](/t/base-snaps/11198) is being used, as outlined below:

- [base: core20](#heading--core20)
- [base: core18 | core](#heading--core18)

For examples, search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+qmake%22&type=Code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.

<h3 id='heading--core20'>base: core20</h3>

This plugin uses the following plugin-specific keywords:

- **`qmake-parameters`** (list of strings)
      additional options to pass to the qmake invocation.
- **`qmake-project-file`** (string)
      the qmake project file to use. This is usually only needed if  qmake can not determine what project file to use on its own.

<h3 id='heading--core18'>base: core18 | core</h3>

This plugin uses the following plugin-specific keywords:

- **`options`** (list of strings)
     additional options to pass to the qmake invocation.
- **`qt-version`** (string; default: qt5)
     Version of Qt to use with qmake. Valid options are: `qt4` and `qt5`.
- **`project-files`** (list of strings)
     list of .pro files to pass to the qmake invocation.