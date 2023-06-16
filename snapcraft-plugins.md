.. 4284.md

.. _snapcraft-plugins:

# Snapcraft plugins

Plugins are used by the *snapcraft* command to build a snap from *parts* defined within `snapcraft.yaml`.

Commonly used plugins include *Python*, *Go*, *Java*, *cmake* and *autotools*, and these help when working with projects written in a specific language or with a specific set of build tools.

These, and many other plugins, are included with Snapcraft, all of which can be listed with the following command:

```bash
$ snapcraft list-plugins
Displaying plugins available for 'core20'
autotools  cmake  dump  go  make  meson  nil  npm  python  rust
```

With Snapcraft 4.0, if the working directory contains a Snapcraft project, the default behaviour is to show only the plugins available for either its specified base or the latest available supported base (currently `core20`).

To list plugins specific to a defined base, run the following command:

```bash
$ snapcraft list-plugins --base core18
Displaying plugins available for 'core18'
ant           cmake    dotnet   godeps  make   nodejs             ruby
autotools     colcon   dump     gradle  maven  plainbox-provider  rust
catkin        conda    flutter  kbuild  meson  python             scons
catkin-tools  crystal  go       kernel  nil    qmake              waf

```

Further information about any specific plugin can be obtained by typing `snapcraft help` followed by the plugin name:

```bash
$ snapcraft help python
```

With Snapcraft 4.0, the help command is also base aware. To get help for a plugin targeting a specific base, run:

```bash
$ snapcraft help python --base core18
```

For further details on specific plugins, see [Supported plugins](/t/supported-plugins/8080), and to create your own, see [Writing local plugins](/t/writing-local-plugins/5125).

<!-- TODO: Move the following to the 'Writing local plugins* document

When building a snap, Snapcraft advances through the following steps to incorporate a snap's plugins:

1. **pull**: retrieves the source for the part from the specified location
1. **build**: drives the build system, determined by the choice of plugin
1. **stage**: consolidates desirable files from all parts into one tree
1. **prime**: removes any unnecessary files, leaving only those required by the snap
1. **snap**: compresses the prime file tree into an installable snap file

Each step corresponds to a *snapcraft* command. When you initiate `snapcraft pull`, for instance, the source is pulled for each plugin within each part in the snap. Each part will then have a fully populated `parts/<part-name/>/src/` directory. Similarly, `snapcraft build` invokes a plugin's build process for each part in turn.

-->