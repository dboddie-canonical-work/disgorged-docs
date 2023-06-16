.. 12530.md

.. _the-conda-plugin:

# The conda plugin

The `conda` plugin is useful, primarily, for Python parts using the [Conda](https://docs.conda.io) open source package management system.

This plugin uses the common plugin keywords as well as those for "sources". For more information, see [Snapcraft parts metadata](snapcraft-parts-metadata.md).

Additional features and syntax are dependent on which [base](base-snaps.md) is being used, as outlined below:

- [base: core22](#heading--core22)
- [base: core20](#heading--core20)
- [base: core18 | core](#heading--core18)

For examples, search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+conda%22&type=Code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](snapcraft-plugins.md) and [Supported plugins](supported-plugins.md) for further details on how plugins are used.

<h3 id='heading--core22'>base: core22</h3>

This plugin uses the following plugin-specific keywords:
* **`conda-packages`** (list of strings)
List of *conda* packages to install.
* **`conda-python-version`** (string)
The Python version to use for the *conda* packages.
Python version major and minor version (e.g. 3.9).
* **`conda-miniconda-version`** (string, default: _latest_)
The version of [Miniconda](https://docs.conda.io/en/latest/miniconda.html) to bootstrap.
Defaults to the latest release.

Requires Snapcraft version *7.0+* .

<h3 id='heading--core20'>base: core20</h3>

This plugin uses the following plugin-specific keywords:
* **`conda-packages`** (list of strings)
List of *conda* packages to install.
* **`conda-python-version`** (string)
The Python version to use for the *conda* packages.
Python version major and minor version (e.g. 3.9).
* **`conda-miniconda-version`** (string, default: _latest_)
The version of [Miniconda](https://docs.conda.io/en/latest/miniconda.html) to bootstrap.
Defaults to the latest release.

Requires Snapcraft version *4.6+* .

<h3 id='heading--core18'>base: core18 | core</h3>

This plugin uses the following plugin-specific keywords:
-   **`conda-packages`** (list of strings)
    List of *conda* packages to install.
-   **`conda-python-version`** (string)
    The Python version to use for the *conda* packages.
    Defaults to the latest supported by [Miniconda](https://docs.conda.io/en/latest/miniconda.html).
-   **`conda-miniconda-version`** (string)
    The version of [Miniconda](https://docs.conda.io/en/latest/miniconda.html) to bootstrap.
    Defaults to the latest release.