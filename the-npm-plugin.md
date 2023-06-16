.. 17591.md

.. _the-npm-plugin:

# The npm plugin

The npm plugin is useful when working with [Node.js](https://nodejs.org/en/) and [npm](https://www.npmjs.com/) JavaScript based parts.

This plugin can only be used with a [base](https://forum.snapcraft.io/t/base-snaps/11198) of `core22` and `core20`. For  `core18` and `core`, use the [nodejs](/t/the-nodejs-plugin/8514) plugin instead.

The plugin uses *node* to install dependencies from `package.json`. It also sets up binaries defined in `package.json` by adding them to `PATH`.

This plugin uses the common plugin keywords as well as those for "sources". For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).

Plugin-specific features and syntax are dependent on which [base](/t/base-snaps/11198) is being used, as outlined below:

- [base: core22](#heading--core22)
- [base: core20](#heading--core20)


See [Node applications](https://snapcraft.io/docs/node-apps)
for a simple example, or search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+npm%22&type=Code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.

<h3 id='heading--core22'>base: core22</h3>

This plugin uses the following plugin-specific keyword:

- **`npm-include-node`** (bool, default: _false_)
      If true, download and include the _node_ binary and its dependencies.  If `npm-include-node` is true, then `npm-node-version` must be defined.

- **`npm-node-version`** (string)
      The version of *node.js* you want the snap to run on and includes _npm_, as would be downloaded from (https://nodejs.org).

Requires Snapcraft version _7.0+_.

<h3 id='heading--core20'>base: core20</h3>

This plugin uses the following plugin-specific keyword:

- **`npm-node-version`** (string)
      The version of *node.js* you want the snap to run on and includes _npm_, as would be downloaded from (https://nodejs.org).

Requires Snapcraft version _4.0+_.