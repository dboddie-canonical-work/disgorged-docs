.. 12530.md

.. \_the-conda-plugin:

The conda plugin
================

The ``conda`` plugin is useful, primarily, for Python parts using the `Conda <https://docs.conda.io>`__ open source package management system.

This plugin uses the common plugin keywords as well as those for “sources”. For more information, see `Snapcraft parts metadata <snapcraft-parts-metadata.md>`__.

Additional features and syntax are dependent on which `base <base-snaps.md>`__ is being used, as outlined below:

-  `base: core22 <#the-conda-plugin-heading--core22>`__
-  `base: core20 <#the-conda-plugin-heading--core20>`__
-  `base: core18 \| core <#the-conda-plugin-heading--core18>`__

For examples, search `GitHub <https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+conda%22&type=Code>`__ for projects already using the plugin.

   ⓘ This is a *snapcraft* plugin. See `Snapcraft plugins <snapcraft-plugins.md>`__ and `Supported plugins <supported-plugins.md>`__ for further details on how plugins are used.

.. raw:: html

   <h3 id="the-conda-plugin-heading--core22">

base: core22

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keywords: \* **``conda-packages``** (list of strings) List of *conda* packages to install. \* **``conda-python-version``** (string) The Python version to use for the *conda* packages. Python version major and minor version (e.g. 3.9). \* **``conda-miniconda-version``** (string, default: *latest*) The version of `Miniconda <https://docs.conda.io/en/latest/miniconda.html>`__ to bootstrap. Defaults to the latest release.

Requires Snapcraft version *7.0+* .

.. raw:: html

   <h3 id="the-conda-plugin-heading--core20">

base: core20

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keywords: \* **``conda-packages``** (list of strings) List of *conda* packages to install. \* **``conda-python-version``** (string) The Python version to use for the *conda* packages. Python version major and minor version (e.g. 3.9). \* **``conda-miniconda-version``** (string, default: *latest*) The version of `Miniconda <https://docs.conda.io/en/latest/miniconda.html>`__ to bootstrap. Defaults to the latest release.

Requires Snapcraft version *4.6+* .

.. raw:: html

   <h3 id="the-conda-plugin-heading--core18">

base: core18 \| core

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keywords: - **``conda-packages``** (list of strings) List of *conda* packages to install. - **``conda-python-version``** (string) The Python version to use for the *conda* packages. Defaults to the latest supported by `Miniconda <https://docs.conda.io/en/latest/miniconda.html>`__. - **``conda-miniconda-version``** (string) The version of `Miniconda <https://docs.conda.io/en/latest/miniconda.html>`__ to bootstrap. Defaults to the latest release.
