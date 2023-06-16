.. 12527.md

.. _the-crystal-plugin:

# The crystal plugin

The `crystal` plugin is useful for parts using the [Crystal](https://crystal-lang.org/) programming language with the  [Crystal snap](https://snapcraft.io/crystal).  This plugin uses the common plugin keywords as well as those for [sources](snapcraft-parts-metadata.md#the-crystal-plugin-heading--source). For more information, see [Snapcraft parts metadata](snapcraft-parts-metadata.md).


Plugin-specific features and syntax are dependent on which [base](base-snaps.md) is being used, as outlined below:

- [base: core20](#the-crystal-plugin-heading--core20)
- [base: core18 | core](#the-crystal-plugin-heading--core18)

For examples, search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+crystal%22&type=Code) for projects already using the plugin.

Brian J. Cardiff, one of Crystal's developers, attended the 2019 Snapcraft Summit Montréal and wrote an excellent overview of how to use the plugin as part of an event write-up. See [Snapcraft Summit Montréal](https://crystal-lang.org/2019/06/19/snapcraft-summit-montreal.html) for the post.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](snapcraft-plugins.md) and [Supported plugins](supported-plugins.md) for further details on how plugins are used.

<h3 id='the-crystal-plugin-heading--core20'>base: core20</h3>

This plugin uses the following plugin-specific keywords:
-   **`crystal-channel`**: (string, default: _latest/stable_)
    The Snap Store channel to install Crystal from.

-   **`crystal-build-options`**: (list)
    Command line options to pass to `shards build`. (e.g. `[--release, --static]`)

Requires Snapcraft version _7.0+_.

<h3 id='the-crystal-plugin-heading--core18'>base: core18 | core</h3>

The following keyword is currently accepted by the plugin:
-   **`crystal-channel`**: (string, default: _latest/stable_)
    The Snap Store channel to install Crystal from.

Requires Snapcraft version _3.7+_.