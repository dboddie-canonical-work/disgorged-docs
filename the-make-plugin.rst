.. 8622.md

.. \_the-make-plugin:

The make plugin
===============

The ``make`` plugin is useful when building `make <https://www.gnu.org/software/make/manual/make.html>`__-based parts. Make-based projects will typically include a *Makefile* that drives the build.

This plugin runs ‘make’ followed by ‘make install’, except when the ``artifacts`` keyword is used with *core18* or *core*.

If your project uses `Automake <https://www.gnu.org/software/automake/>`__, take a look at the `autotools <the-autotools-plugin.md>`__ plugin. For examples, search `GitHub <https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+make%22&type=Code>`__ for projects using the plugin.

This plugin uses the common plugin keywords as well as those for “sources”. For more information, see `Snapcraft parts metadata <snapcraft-parts-metadata.md>`__.

Its features and syntax are dependent on which `base <base-snaps.md>`__ is being used, as outlined below:

-  `base: core22 <#the-make-plugin-heading--core22>`__
-  `base: core20 <#the-make-plugin-heading--core20>`__
-  `base: core18 \| core <#the-make-plugin-heading--core18>`__

..

   ⓘ This is a *snapcraft* plugin. See `Snapcraft plugins <snapcraft-plugins.md>`__ and `Supported plugins <supported-plugins.md>`__ for further details on how plugins are used.

.. raw:: html

   <h3 id="the-make-plugin-heading--core22">

base: core22

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keywords:

-  **``make-parameters``** (list of strings) Parameters to pass to the make command.

Use Snapcraft’s `override-build <snapcraft-parts-metadata.md#the-make-plugin-heading--override-build>`__ functionality to implement the equivalent ``makefile``, ``artifacts`` and ``make-install-var`` functionality available to *core18* and *core* snaps.

Requires Snapcraft version *7.0+*.

.. raw:: html

   <h3 id="the-make-plugin-heading--core20">

base: core20

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keywords:

-  **``make-parameters``** (list of strings) Parameters to pass to the make command.

Use Snapcraft’s `override-build <snapcraft-parts-metadata.md#the-make-plugin-heading--override-build>`__ functionality to implement the equivalent ``makefile``, ``artifacts`` and ``make-install-var`` functionality available to *core18* and *core* snaps.

Requires Snapcraft version *4.0+*.

.. raw:: html

   <h3 id="the-make-plugin-heading--core18">

base: core18 \| core

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keywords:

-  **``artifacts``** (list) Link/copy the given files from the *make* output to the snap installation directory. If specified, the ``make install`` step will be skipped.

-  **``makefile``** (string) Use the given file as the *makefile*.

-  **``make-parameters``** (list of strings) Parameters to pass to the make command.

-  **``make-install-var``** (string; default: DESTDIR) Use this variable to redirect the installation into the snap.

Requires Snapcraft version *3.x*.
