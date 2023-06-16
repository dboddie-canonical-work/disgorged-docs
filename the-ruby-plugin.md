.. 8587.md

.. _the-ruby-plugin:

# The ruby plugin

The `ruby` plugin is useful for [Ruby](https://www.ruby-lang.org/en/)-based parts.  This plugin uses the common plugin keywords as well as those for [sources](/t/snapcraft-parts-metadata/8336#heading--source). For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).


> ⓘ This plugin is only available to _core_ and _core18_ based snaps. See [Base snaps](/t/base-snaps/11198) for details.

The [gem](https://guides.rubygems.org/command-reference/#gem-install) package manager and an associated [Gemfile](https://bundler.io/man/gemfile.5.html) are used to install dependencies.

See [Ruby applications](https://snapcraft.io/docs/ruby-applications) for a simple example, or search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+ruby%22&type=Code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.

This plugin uses the following plugin-specific keywords:

- **`gems`** (list)
      A list of gems to install.
- **`use-bundler`** (boolean)
      Use bundler to install gems from a Gemfile (defaults to 'false').
- **`ruby-version`** (string)
      The version of ruby you want this snap to run.