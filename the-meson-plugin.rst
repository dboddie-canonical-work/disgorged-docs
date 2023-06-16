.. 8623.md

.. \_the-meson-plugin:

The meson plugin
================

The ``meson`` plugin is useful for building `Meson <https://mesonbuild.com/>`__-based parts.

Projects using the Meson build system will contain a *meson.build* file that drives the build, and the plugin runs the following commands to build your project:

1. ``meson``
2. ``ninja``
3. ``ninja install``

This plugin uses the common plugin keywords as well as those for `sources <snapcraft-parts-metadata.md#the-meson-plugin-heading--source>`__. For more information, see `Snapcraft parts metadata <snapcraft-parts-metadata.md>`__.

For examples, search `GitHub <https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+meson%22&type=Code>`__ for projects using the plugin.

Plugin-specific features and syntax are dependent on which `base <base-snaps.md>`__ is being used, as outlined below:

-  `base: core22 <#the-meson-plugin-heading--core22>`__
-  `base: core20 <#the-meson-plugin-heading--core20>`__
-  `base: core18 \| core <#the-meson-plugin-heading--core18>`__

..

   ⓘ This is a *snapcraft* plugin. See `Snapcraft plugins <snapcraft-plugins.md>`__ and `Supported plugins <supported-plugins.md>`__ for further details on how plugins are used.

.. raw:: html

   <h3 id="the-meson-plugin-heading--core22">

base: core22

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keywords:

-  **``meson-parameters``** (list of strings) List of parameters to pass to the *meson* command.

Requires Snapcraft version *7.0+*.

.. raw:: html

   <h3 id="the-meson-plugin-heading--core20">

base: core20

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keywords:

-  **``meson-parameters``** (list of strings) List of parameters to pass to the *meson* command.

-  **``meson-version``** (string) Version of *meson* to download from `PyPI <https://pypi.org/project/meson/>`__ (e.g. 0.62.1).

Requires Snapcraft version *4.0+*.

.. raw:: html

   <h3 id="the-meson-plugin-heading--core18">

base: core18 \| core

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keywords:

-  **``meson-parameters``** (list of strings) List of parameters to pass to the *meson* command.

-  **``meson-version``** (string) Version of *meson* to download from `PyPI <https://pypi.org/project/meson/>`__ (e.g. 0.62.1).
