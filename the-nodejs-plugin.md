.. 8514.md

.. _the-nodejs-plugin:

# The nodejs plugin

The `nodejs` plugin is useful when working with [Node.js](https://nodejs.org/en/) and [npm](https://www.npmjs.com/) JavaScript based parts.

This plugin can only be used with a [base](/t/base-snaps/11198)  of either `core18` and `core`. For `core20` and `core22`, use the [npm](/t/the-npm-plugin/17591) plugin instead.

Additional features and syntax are dependent on which [base](/t/base-snaps/11198) is being used, as outlined below:

The plugin uses *node* to install dependencies from `package.json`. It also sets up binaries defined in `package.json` by adding them to `PATH`.

This plugin uses the common plugin keywords as well as those for "sources". For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).

<h3 id='heading--core18'>base: core18 | core</h3>

This plugin uses the following plugin-specific keywords:

- **`nodejs-version`** (string; default: 8.12.0)
      The version of *node.js* you want the snap to run on. For example: `nodejs-version: 8.12.0`
- **`nodejs-package-manager`** (string; default: yarn)
      The language package manager to use to drive installation of node packages. Can be either `npm` or `yarn` (default).
- **`nodejs-yarn-version`** (string)
      The version of the _yarn_ package manager to use to drive installation of node packages.  Currently, this must start with a _v_, for example: `nodejs-yarn-version: v1.19.1`

For examples, search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+nodejs%22&type=Code) for projects already using the plugin.

Requires Snapcraft version _3.x_.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.