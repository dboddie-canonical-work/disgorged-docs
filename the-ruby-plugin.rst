.. 8587.md

.. \_the-ruby-plugin:

The ruby plugin
===============

The ``ruby`` plugin is useful for `Ruby <https://www.ruby-lang.org/en/>`__-based parts. This plugin uses the common plugin keywords as well as those for `sources <snapcraft-parts-metadata.md#the-ruby-plugin-heading--source>`__. For more information, see `Snapcraft parts metadata <snapcraft-parts-metadata.md>`__.

   ⓘ This plugin is only available to *core* and *core18* based snaps. See `Base snaps <base-snaps.md>`__ for details.

The `gem <https://guides.rubygems.org/command-reference/#gem-install>`__ package manager and an associated `Gemfile <https://bundler.io/man/gemfile.5.html>`__ are used to install dependencies.

See `Ruby applications <https://snapcraft.io/docs/ruby-applications>`__ for a simple example, or search `GitHub <https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+ruby%22&type=Code>`__ for projects already using the plugin.

   ⓘ This is a *snapcraft* plugin. See `Snapcraft plugins <snapcraft-plugins.md>`__ and `Supported plugins <supported-plugins.md>`__ for further details on how plugins are used.

This plugin uses the following plugin-specific keywords:

-  **``gems``** (list) A list of gems to install.
-  **``use-bundler``** (boolean) Use bundler to install gems from a Gemfile (defaults to ‘false’).
-  **``ruby-version``** (string) The version of ruby you want this snap to run.
