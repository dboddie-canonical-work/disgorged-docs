.. 12509.md

.. _release-notes-snapcraft-3-7:

# Release notes: Snapcraft 3.7

These are the release notes for [Snapcraft 3.7](https://github.com/snapcore/snapcraft/releases/tag/3.7), a significant update to [Snapcraft 3](/t/snapcraft-overview/8940).

For general details, including installation instructions, see [Snapcraft overview](/t/snapcraft-overview/8940), or take a look at [Snapcraft release notes](/t/snapcraft-release-notes/10721) for other *Snapcraft* releases.

> ℹ Many of the improvements in this release are thanks to the great work done in collaboration with the attendees of the [2019 Snapcraft Summit](https://snapcraft.io/blog/snapcraft-summit-montreal) that took place in Montreal.

## New *core* features

### Extended build options

**_build-base_**

Prior to the release of Snapcraft 3.7, using the `base` keyword within `snapcraft.yaml` to specify a base type for a snap did not take into account the *creation* of bases. Instead, the `name` keyword was arbitrarily used to determine the build environment:

```yaml
name: core18
type: base
# base: is not set elsewhere
```

The above example uses `name` to specify the creation of an Ubuntu 18.04 (core18) based build environment.

This fails if a base has yet to be bootstrapped, or is otherwise unavailable. For example, the following will currently generate a `launch failed: Unable to find an image matching "core20" error:

```yaml
name: core20
type: base
# base: is not set elsewhere
```

In cases like the above, where the base has not yet been bootstrapped, `build-base` can be used to explicitly define the base to use for the build environment.

To solve the above issue, for example, use the following:

```yaml
name: core20
type: base
build-base: core18
# base: is not set elsewhere
```


**_snapd_**

`snapd` is a new value for *base type*. Its inclusion will help the *snapd* team when using Snapcraft to build their own snap.

### Extended metadata

The [snapcraft.yaml](/t/the-snapcraft-format/8337) schema has been extended to support new app properties added to [snap.yaml](/t/the-snap-format/698), alongside better error handling and schema checks.

- It's now possible to specify the *type* string for the following existing options with an unspecified type:
    -   `stop-command`
    -   `reload-command`
- Daemon options:
    - New daemon type: `dbus`
    - `bus-name` (for use with `daemon: dbus`). Uses [regex pattern](https://github.com/snapcore/snapcraft/pull/2627#issuecomment-515550633) found in snapd
    - `restart-delay`
    - `start-timeout`
    - `timer`
    - `watchdog-timeout`
    - daemon dependencies can be specified as well as existing options (`stop-timeout`, `restart-condition`)
- `on-watchdog` for `restart-condition`
- `autostart` for apps installing autostart desktop files
-  [regex patterns](https://github.com/snapcore/snapcraft/pull/2627#issuecomment-515550633) added to `stop-timeout` (to match introduced timeouts).

### Faster LXD build iterations

When using [Snapcraft with LXD](t/build-on-lxd/4157) and [iterating over a build](/t/iterating-over-a-build/12143), a significant reduction in network overhead has resulted in much faster build times.

This is thanks to *snapd 2.39* supporting API snap retrieval, and is used to avoid a root requirement when adding snaps to the build environment. It means snap don't need to be re-downloaded as frequently.

### Improved missing file experience

After the [prime stage](t/snapcraft-lifecycle/5123) has completed, and missing dependencies are detected, Snapcraft now lists these as _stage-packages_, rather than as a simple list, for inclusion in *snapcraft.yaml* to hopefully build a functioning snap.

This will be extended in upcoming versions of Snapcraft to take into account plugs using the `content` interface.

## Plugins

### crystal (new plugin)

[Crystal](https://crystal-lang.org/) is a programming language with a similar syntax to Ruby. This plugin was developed by Crystal's upstream team to work with their recently released [Crystal snap](https://snapcraft.io/crystal).

The following keyword is currently accepted by the plugin:

-   **`crystal-channel`**: (string)
    The Snap Store channel to install Crystal from.
    Default: `latest/stable`

Brian J. Cardiff, one of Crystal's developers, attended the 2019 Snapcraft Summit Montréal and wrote an excellent overview of how to use the plugin as part of an event write-up. See [Snapcraft Summit Montréal](https://crystal-lang.org/2019/06/19/snapcraft-summit-montreal.html) for the post.

### conda (new plugin)

[Conda](https://docs.conda.io) is an open source package management system and environment management system that runs on Windows, macOS and Linux. This plugin was developed during the  2019 Snapcraft Summit Montréal with the [Anaconda](https://www.anaconda.com/) developers.

This plugin uses the following plugin-specific keywords:
-   **`conda-packages`** (list of strings)
    List of *conda* packages to install.
-   **`conda-python-version`** (string)
    The Python version to use for the *conda* packages.
    Defaults to the latest supported by [Miniconda](https://docs.conda.io/en/latest/miniconda.html).
-   **`conda-miniconda-version`** (string)
    The version of [Miniconda](https://docs.conda.io/en/latest/miniconda.html) to bootstrap.
    Defaults to the latest release.

### rust

The [Rust plugin](/t/the-rust-plugin/8588) has been reviewed by a Rust developer and their suggestions incorporated into this release.

One such improvement is defaulting to use the `rust-toolchain` file (if present), unless explicitly overridden by use of `rust-channel` or `rust-revision`.

Rebuilding is now also possible using this plugin.

### ant

The [Ant](https://ant.apache.org/) publisher has released an [Ant snap](https://snapcraft.io/ant) and reviewed the [Ant plugin](/t/the-ant-plugin/8507). Consequently, the Ant plugin has been updated to support the use of this new snap for building Ant-based projects.

The following new keywords are now accepted by the plugin:

-   **`ant-channel`** (string)
    If not using the Ant tarball from the Ant archive (see [ant-version and ant-version-checksum](/t/the-ant-plugin/8507), this keyword specifies the channel to use for *ant* in the Snap Store.
   Default: `latest/stable`

### colcon

Support for [ROS 2 Dashing Diademata](https://index.ros.org//doc/ros2/Releases/Release-Dashing-Diademata/) was added to the [colcon](/t/the-colcon-plugin/11895) plugin in order to support this latest ROS release.

## Bug fixes

There have been many bugs fixed in this release. Some of the most significant are as follows:
-   improved error handling
-   additional AppStream icon extraction scenarios that are now taken into account
-   modified handling of in-snap symlinks, specifically to better accommodate the merged `/usr` directory scheme
-   `click.prompt` and `click.confirm` expanded to query the existence of tty for stdin.

## Full list of changes

The full list of features and issues worked on in this release are listed below.

[details=List of changes for Snapcraft 3.7]


#### Sergio Schvezov

-   static: use beta channel for black ([#2606](https://github.com/snapcore/snapcraft/pull/2606))
-   catkin spread tests: dump apt-config on failures for legacy ([#2610](https://github.com/snapcore/snapcraft/pull/2610))
-   rust plugin: use toml to dump the config ([#2611](https://github.com/snapcore/snapcraft/pull/2611))
-   rust plugin: use rust-toolchain by default if present ([#2613](https://github.com/snapcore/snapcraft/pull/2613))
-   conda plugin: new plugin ([#2608](https://github.com/snapcore/snapcraft/pull/2608))
-   build providers: support injection for LXD ([#2621](https://github.com/snapcore/snapcraft/pull/2621))
-   schema: remove support for os when using bases ([#2626](https://github.com/snapcore/snapcraft/pull/2626))
-   appstream extractor: skip non icon file paths ([#2630](https://github.com/snapcore/snapcraft/pull/2630))
-   spread tests: enable LXD build provider tests ([#2631](https://github.com/snapcore/snapcraft/pull/2631))
-   build environment: detect base type and use name as base
-   plugins: use get_build_base to determine base support
-   project: add support for build-base
-   repo: add support for querying file ownership
-   pluginhandler: suggest stage-packages for missing DT_NEEDED
-   tests: add python3-toml for autopkgtests
-   spread tests: limit conda plugin to non autopkgtests x86-64 systems
-   spread tests: crystal tests should only run on x86-64

#### Chris Patterson

-   black: minor format changes from updated black ([#2603](https://github.com/snapcore/snapcraft/pull/2603))
-   sources: introduce SnapcraftSourceNotFoundError ([#2604](https://github.com/snapcore/snapcraft/pull/2604))
-   spread: use more workers to reduce job times
-   catkin/legacy-pull: set test to manual
-   cli: convert users of click.confirm/prompt to echo.confirm/prompt
-   echo: respect SNAPCRAFT_HAS_TTY for is_tty_connected()
-   ant plugin: switch to using ant snap for building (by default)
-   general spread tests: set base for cwd test ([#2618](https://github.com/snapcore/snapcraft/pull/2618))
-   errors: refactor exception/error handling ([#2602](https://github.com/snapcore/snapcraft/pull/2602))
-   tests/unit/pluginhandler: introduce tests to repro symlink preservation bug
-   file_utils/create_similar_directory: drop follow_symlinks option
-   pluginhandler: honour symlink directory paths for filesets (LP: #1833408)
-   test_pluginhandler: remove faulty (redundant) tests
-   schema: synchronizing snapd supported schema to snapcraft ([#2627](https://github.com/snapcore/snapcraft/pull/2627))

#### Brian J. Cardiff

-   crystal plugin: new plugin ([#2598](https://github.com/snapcore/snapcraft/pull/2598))

#### Mike Miller

-   build providers: enforce well-known temp dir ([#2607](https://github.com/snapcore/snapcraft/pull/2607)) (LP: #1833292)

#### Pawel Stolowski

-   schema: allow snapd as snap type ([#2609](https://github.com/snapcore/snapcraft/pull/2609))

#### Claudio Matsuoka

-   echo: add wrappers for click.prompt() and click.confirm()

#### Kyle Fazzari

-   colcon plugin: add support for dashing ([#2593](https://github.com/snapcore/snapcraft/pull/2593))

#### Anatoly Techtonik

-   cli: add -h short option for help ([#2527](https://github.com/snapcore/snapcraft/pull/2527)) (LP: #1807423)

#### Stefan Bodewig

-   use the stable risk level now that ant has been released

#### Chris MacNaughton

-   rust plugin: add ability to rebuild ([#2620](https://github.com/snapcore/snapcraft/pull/2620)) (LP: #1825858)

#### Carlo Lobrano

-   tools: let environment-setup.sh skip unnecessary steps ([#2625](https://github.com/snapcore/snapcraft/pull/2625))

[/details]