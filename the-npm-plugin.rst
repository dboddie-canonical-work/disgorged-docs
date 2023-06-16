.. 17591.md

.. \_the-npm-plugin:

The npm plugin
==============

The npm plugin is useful when working with `Node.js <https://nodejs.org/en/>`__ and `npm <https://www.npmjs.com/>`__ JavaScript based parts.

This plugin can only be used with a `base <base-snaps.md>`__ of ``core22`` and ``core20``. For ``core18`` and ``core``, use the `nodejs <the-nodejs-plugin.md>`__ plugin instead.

The plugin uses *node* to install dependencies from ``package.json``. It also sets up binaries defined in ``package.json`` by adding them to ``PATH``.

This plugin uses the common plugin keywords as well as those for “sources”. For more information, see `Snapcraft parts metadata <snapcraft-parts-metadata.md>`__.

Plugin-specific features and syntax are dependent on which `base <base-snaps.md>`__ is being used, as outlined below:

-  `base: core22 <#the-npm-plugin-heading--core22>`__
-  `base: core20 <#the-npm-plugin-heading--core20>`__

See `Node applications <https://snapcraft.io/docs/node-apps>`__ for a simple example, or search `GitHub <https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+npm%22&type=Code>`__ for projects already using the plugin.

   ⓘ This is a *snapcraft* plugin. See `Snapcraft plugins <snapcraft-plugins.md>`__ and `Supported plugins <supported-plugins.md>`__ for further details on how plugins are used.

.. raw:: html

   <h3 id="the-npm-plugin-heading--core22">

base: core22

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keyword:

-  **``npm-include-node``** (bool, default: *false*) If true, download and include the *node* binary and its dependencies. If ``npm-include-node`` is true, then ``npm-node-version`` must be defined.

-  **``npm-node-version``** (string) The version of *node.js* you want the snap to run on and includes *npm*, as would be downloaded from (https://nodejs.org).

Requires Snapcraft version *7.0+*.

.. raw:: html

   <h3 id="the-npm-plugin-heading--core20">

base: core20

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keyword:

-  **``npm-node-version``** (string) The version of *node.js* you want the snap to run on and includes *npm*, as would be downloaded from (https://nodejs.org).

Requires Snapcraft version *4.0+*.
