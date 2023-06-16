.. 8529.md

.. _the-python-plugin:

# The python plugin

The `python` plugin can be used by either Python 2 or Python 3 based parts using a `setup.py` script for building the project, or using a package published to PyPI, and optionally any of the following:

- a *requirements.txt* file used to import Python modules
- packages installed directly from *pip*

This plugin uses the common plugin keywords as well as those for "sources". For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).

Plugin-specific features and syntax are dependent on which [base](/t/base-snaps/11198) is being used, as outlined below:

- [base: core22](#heading--core22)
- [base: core20](#heading--core20)
- [base: core18 | core](#heading--core18)

See [Python applications](/t/python-apps/6741) for a simple example, or search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+python%22&type=Code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.

<h3 id='heading--core22'>base: core22</h3>

This plugin uses the following plugin-specific keywords:

- **`python-requirements`** (list)
  List of paths to requirements.txt file(s)
- **`python-constraints`** (list)
  List of paths to constraint files.
- **`python-packages`** (list, default: _[pip, setuptools, wheel]_)</br>
  A list of dependencies to install using `pip`. This supports the same syntax as the `pip install` command.

This plugin also interprets these specific build-environment entries:

- `PARTS_PYTHON_INTERPRETER`
  (default: _python3_)
  The interpreter binary to search for in `PATH`.

- `PARTS_PYTHON_VENV_ARGS`
  Additional arguments for venv.

By default, this plugin uses Python from the base snap. If a part using this plugin uses a build-base other than that of the base, or a different interpreter is desired, it must be bundled in the snap (including _venv_) and must be in PATH.

It is required to bundle _python_ when creating a snap that uses classic confinement, this can be accomplished on Ubuntu by adding stage-packages (i.e.; python3-venv).

Use of python3-<python-package> in stage-packages will force the inclusion of the python interpreter.

Requires Snapcraft version _7.0+_.

<h3 id='heading--core20'>base: core20</h3>

This plugin uses the following plugin-specific keywords:

- **`requirements`** (array)
  List of paths to requirements.txt file(s)
- **`constraints`** (string)
  Path to a constraints file.
- **`python-packages`** (list)
  A list of dependencies to install using `pip`. This supports the same syntax as the `pip install` command.

This plugin also interprets these specific build-environment entries:

- `SNAPCRAFT_PYTHON_INTERPRETER`
  (default: _python3_)
  The interpreter binary to search for in `PATH`.

- `SNAPCRAFT_PYTHON_VENV_ARGS`
  Additional arguments for venv.

By default, this plugin uses Python from the base snap. If a part using this plugin uses a build-base other than that of the base, or a different interpreter is desired, it must be bundled in the snap (including _venv_) and must be in PATH.

It is required to bundle _python_ when creating a snap that uses classic confinement, this can be accomplished on Ubuntu by adding stage-packages (i.e.; python3-venv).

Use of python3-<python-package> in stage-packages will force the inclusion of the python interpreter.

Requires Snapcraft version _4.0+_.

<h3 id='heading--core18'>base: core18 | core</h3>

This plugin uses the following plugin-specific keywords:

- **`requirements`** (array)
  List of paths to requirements.txt file(s)
- **`constraints`** (string)
  Path to a constraints file
- **`process-dependency-links`** (bool; default: false)
  Enable the processing of dependency links in pip, which allow one
  project to provide places to look for another project
- **`python-packages`** (list)
  A list of dependencies to install using `pip`. This supports the same syntax as the `pip install` command. For example:

  ```yaml
  python-packages:
    - docopt == 0.6.1  # Install specific versions
    - git+https://github.com/inuits/mkdocs-factsheet.git  # Install from a git repository
    - https://github.com/cmacmackin/markdown-include/archive/v0.5.1.tar.gz  # Install from an archive
  ```

  See the [`pip install` docs](https://pip.pypa.io/en/stable/reference/pip_install/#pip-install) for more information.
- **`python-version`** (string; default: `python3`)
  The python version to use. Valid options are `python2` and `python3`

The `python` plugin also searches `<stage-dir>/usr/bin/<python-interpreter>` for a Python interpreter with a basename matching `python-version` in the `<stage>` directory. If detected, this takes preference and  `stage-packages` will not use its own interpreter.