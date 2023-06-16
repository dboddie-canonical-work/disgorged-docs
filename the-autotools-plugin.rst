.. 8616.md

.. \_the-autotools-plugin:

The autotools plugin
====================

The ``autotools`` plugin is useful for `Automake/Autotools <https://www.gnu.org/software/automake/>`__ based parts.

Autotools-based projects are easy to recognise, as they’re typically built and installed with the following commands: ``./configure && make && make install``.

This plugin uses the common plugin keywords as well as those for `sources <snapcraft-parts-metadata.md#the-autotools-plugin-heading--source>`__. For more information, see `Snapcraft parts metadata <snapcraft-parts-metadata.md>`__.

Additional features and syntax are dependent on which `base <base-snaps.md>`__ is being used, as outlined below:

-  `base: core22 <#the-autotools-plugin-heading--core22>`__
-  `base: core20 <#the-autotools-plugin-heading--core20>`__
-  `base: core18 \| core <#the-autotools-plugin-heading--core18>`__

See `C/C++ applications <c-c-applications.md>`__ for a simple example, or search `GitHub <https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+autotools%22&type=Code>`__ for projects already using the plugin.

   ⓘ This is a *snapcraft* plugin. See `Snapcraft plugins <snapcraft-plugins.md>`__ and `Supported plugins <supported-plugins.md>`__ for further details on how plugins are used.

.. raw:: html

   <h3 id="the-autotools-plugin-heading--core22">

base: core22

.. raw:: html

   </h3>

1. the *autotools* plugin first attempts to build the project using ``./configure``
2. if the *configure* script does not yet exist, it will attempt to run ``./autoconf --install``.

-  **``autotools-configure-parameters``** (list of strings) Configure flags to pass to the build such as those shown by running ``./configure --help``

Requires Snapcraft version *7.0+*.

.. raw:: html

   <h3 id="the-autotools-plugin-heading--core20">

base: core20

.. raw:: html

   </h3>

1. the *autotools* plugin first attempts to build the project using ``./configure``
2. if the *configure* script does not yet exist, it will attempt to run ``./autoconf --install``.

In addition, this plugin uses the following plugin-specific keywords:

-  **``autotools-configure-parameters``** (previously *configflags*) (list of strings) Configure flags to pass to the build such as those shown by running ``./configure --help``

Requires Snapcraft version *4.0+*.

.. raw:: html

   <h3 id="the-autotools-plugin-heading--core18">

base: core18 \| core

.. raw:: html

   </h3>

1. the *autotools* plugin first attempts to build the project using ``./configure``.
2. if the *configure* script does not yet exist, it will attempt to run ``./autogen``.
3. if *autogen* doesn’t exist, the plugin will run ``autoreconf``.

In addition, this plugin uses the following plugin-specific keywords:

-  **``configflags``** (list of strings) Configure flags to pass to the build such as those shown by running ``./configure --help``
-  **``install-via``** (enum, ‘destdir’ or ‘prefix’) Whether to install via DESTDIR or by using –prefix (default is ‘destdir’)

Requires Snapcraft version *3.x*.