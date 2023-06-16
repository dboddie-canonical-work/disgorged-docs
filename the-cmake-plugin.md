.. 8621.md

.. _the-cmake-plugin:

# The cmake plugin

The `cmake` plugin is useful for building [CMake](https://cmake.org/)-based parts.  This plugin uses the common plugin keywords as well as those for [sources](/t/snapcraft-parts-metadata/8336#heading--source). For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).

This plugin also supports options from the [make](/t/the-make-plugin/8622) plugin.

A *cmake* project will typically include a *CMakeLists.txt* file to drive the build, and the plugin requires that *CMakeLists.txt* exists within the root of the source tree.

Plugin-specific features and syntax are dependent on which [base](/t/base-snaps/11198) is being used, as outlined below:

- [base: core22](#heading--core22)
- [base: core20](#heading--core20)
- [base: core18 | core](#heading--core18)

For a simple example, see [MOOS applications](/t/moos-applications/7820), or search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+cmake%22&type=Code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.

<h3 id='heading--core22'>base: core22</h3>

- **`cmake-generator`** (string, default: _Unix Makefiles_)
      Determine what native build system is to be used.
      Can be either `Ninja` or `Unix Makefiles` (default).
- **`cmake-parameters`** (list of strings)
     Configure flags to pass to the build using the common *cmake* semantics.

Note that Snapcraft does not specify cmake parameters by default.  A common parameter for parts using the cmake plugin is `CMAKE_INSTALL_PREFIX=/usr` - this prevents installation to the default directory of `/usr/local`. For example:

```
parts:
  hello:
    plugin: cmake
    cmake-parameters:
      - -DCMAKE_INSTALL_PREFIX=/usr
    ....
```

Requires Snapcraft version _7.0+_.

<h3 id='heading--core20'>base: core20</h3>

- **`cmake-generator`** (string, default: _Unix Makefiles_)
      Determine what native build system is to be used.
      Can be either `Ninja` or `Unix Makefiles` (default).
- **`cmake-parameters`** (list of strings)
     Configure flags to pass to the build using the common *cmake* semantics.

Note that Snapcraft does not specify cmake parameters by default.  A common parameter for parts using the cmake plugin is `CMAKE_INSTALL_PREFIX=/usr` - this prevents installation to the default directory of `/usr/local`. For example:

```
parts:
  hello:
    plugin: cmake
    cmake-parameters:
      - -DCMAKE_INSTALL_PREFIX=/usr
    ....
```
Requires Snapcraft version _4.0+_.

<h3 id='heading--core18'>base: core18 | core</h3>

- **`configflags`** (list of strings)
     Configure flags to pass to the build using the common *cmake* semantics.

Requires Snapcraft version _3.0+_.