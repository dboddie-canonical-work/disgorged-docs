.. 12271.md

.. _parts-environment-variables:

# Parts environment variables

When building a part to construct a snap,  [Snapcraft](/t/snapcraft-overview/8940) creates the following sets of environment variables that can optionally be used by a part's build mechanism:

- [Locating directories](#heading--locating-directories)
  - [core | core18 | core20](#heading--locating-directories-core18-core20)
  - [core22](#heading--locating-directories-core22)
- [Snapcraft configuration](#heading--snapcraft-configuration)
  - [core | core18 | core20](#heading--snapcraft-configuration-core18-core-20)
  - [core22](#heading--snapcraft-configuration-core22)
- [Build flags](#heading--build-flags)
- [Plugin variables](#heading--plugin-variables)

Environment variables can be accessed via the [*override-*](/t/snapcraft-parts-metadata/8336) keywords with shell commands and [Scriptlets](/t/scriptlets/4892), or more generally within your project's build infrastructure.

See [Adding parts](/t/adding-parts/11473) for a general overview of what parts are and how to use them, and for more details on how parts are built within the *snapcraft* environment, including build stages and the directories they use, see [Parts lifecycle](/t/parts-lifecycle/12231).

> ⓘ For the various environment variables available to running snap applications, see [Environment variables](/t/environment-variables/7983).

<h3 id='heading--locating-directories'>Locating directories</h3>

See [Parts lifecycle](/t/parts-lifecycle/12231) and [Parts directories](/t/parts-lifecycle/12231#heading--parts-directories) for details on which directories are created and used when building a part.

<h4 id='heading--locating-directories-core18-core20'>core | core18 | core20</h4>

Snapcraft exposes the following directory related environment variables when building a part with bases `core`, `core18`, or `core20`. These can help when moving or locating files:
| | |
|--|--|
| `SNAPCRAFT_PART_SRC` | absolute path to where a part's sources are pulled. It's also the part's working directory for the *pull* step |
| `SNAPCRAFT_PART_BUILD` | absolute path to the sources used for the part's *build* step. It is also the working directory of the *build* step. |
| `SNAPCRAFT_PART_INSTALL` | absolute path to the results of the part's *build* step. It also contains the staged packages of that part. |
| `SNAPCRAFT_PRIME` |  absolute path to where files are primed |
|`SNAPCRAFT_PROJECT_DIR`| absolute path to the root of the snapcraft project |
| `SNAPCRAFT_STAGE` | absolute path to where files are staged |

<h4 id='heading--locating-directories-core22'>core22</h4>

Snapcraft exposes the following directory related environment variables when build with base `core22`. These can help when moving or locating files:

| | |
|--|--|
| `CRAFT_PART_SRC` <br /> `SNAPCRAFT_PART_SRC` | absolute path to where a part's sources are pulled. It's also the part's working directory for the *pull* step |
| `CRAFT_PART_SRC_WORK` <br /> `SNAPCRAFT_PART_SRC` | absolute path to the part source subdirectory, if any. Defaults to the part source directory. |
| `CRAFT_PART_BUILD` <br /> `SNAPCRAFT_PART_BUILD` | absolute path to the sources used for the part's *build* step. It is also the working directory of the *build* step. |
| `CRAFT_PART_BUILD_WORK` <br /> `SNAPCRAFT_PART_BUILD_WORK` | absolute path to the part build subdirectory in case of out-of-tree builds. Defaults to the part source directory. |
| `CRAFT_PART_INSTALL` <br /> `SNAPCRAFT_PART_INSTALL` | absolute path to the results of the part's *build* step. It also contains the staged packages of that part. |
| `CRAFT_PRIME` <br /> `SNAPCRAFT_PRIME` |  absolute path to where files are primed |
| `CRAFT_PROJECT_DIR` <br /> `SNAPCRAFT_PROJECT_DIR` | absolute path to the root of the snapcraft project |
| `CRAFT_STAGE` <br /> `SNAPCRAFT_STAGE` | absolute path to where files are staged |
| `CRAFT_OVERLAY` | absolute path the part's layer directory during  the `OVERLAY` step if overlays are enabled. |

<h3 id='heading--snapcraft-configuration'>Snapcraft configuration</h3>

<h4 id='heading--snapcraft-configuration-core18-core-20'>core | core18 | core20</h4>

When building a part with bases `core`, `core18`, or `core20`, the following *snapcraft* environment variables are set:

| | |
|--|--|
| `SNAPCRAFT_ARCH_TRIPLET` | the architecture triplet used for the selected base |
| `SNAPCRAFT_PARALLEL_BUILD_COUNT`| the preferred number of jobs the project is to be built with |
| `SNAPCRAFT_PROJECT_NAME` | the snapcraft project name as set by `name` in `snapcraft.yaml` |
| `SNAPCRAFT_PROJECT_VERSION` | the snapcraft project version as set by `snapcraft.yaml`|
| `SNAPCRAFT_PROJECT_GRADE` | the snapcraft project grade as set in `snapcraft.yaml` |
| `SNAPCRAFT_TARGET_ARCH` | deb-style architecture that snap is being built for, e.g. "amd64", "armhf", "arm64", etc. |

<h4 id='heading--snapcraft-configuration-core22'>core22</h4>

When building a part with base `core22`, the following *snapcraft* environment variables are set:

| | |
|--|--|
| `CRAFT_ARCH_TRIPLET` <br /> `SNAPCRAFT_ARCH_TRIPLET`  | the architecture triplet used for the selected base |
| `CRAFT_PARALLEL_BUILD_COUNT` <br /> `SNAPCRAFT_PARALLEL_BUILD_COUNT`| the preferred number of jobs the project is to be built with |
| `CRAFT_PROJECT_NAME` <br /> `SNAPCRAFT_PROJECT_NAME` | the snapcraft project name as set by `name` in `snapcraft.yaml` |
| `SNAPCRAFT_PROJECT_VERSION` | the snapcraft project version as set by `snapcraft.yaml`|
| `SNAPCRAFT_PROJECT_GRADE` | the snapcraft project grade as set in `snapcraft.yaml` |
| `CRAFT_TARGET_ARCH` <br /> `SNAPCRAFT_TARGET_ARCH` | deb-style architecture that snap is being built for, e.g. "amd64", "armhf", "arm64", etc. |
| `CRAFT_PART_NAME` | the part currently being processed, as set by the part's name in `snapcraft.yaml` |
| `CRAFT_STEP_NAME` | the step currently being executed (i.e. `PRIME`) |

<h3 id='heading--build-flags'>Build flags</h3>

The following specific _build flags_ are also set:

| | |
|--|--|
| `CFLAGS`| empty unless `after` is used in the part and headers are staged in the common include paths for which they will be included (i.e.; paths added with  `-I`)|
|`CPPFLAGS`| same behavior as CFLAGS |
| `CXXFLAGS` | same behavior as CFLAGS |
| `LDFLAGS` | empty unless `after` is used in the part and headers are staged in the common library paths (i.e.; paths added with `-L`) |
| `PKG_CONFIG_PATH` | empty unless `after` is used in the part and .pc files are staged in the common pkgconfig paths |

<h3 id='heading--plugin-variables'>Plugin variables</h3>

A part's [plugin](/t/snapcraft-plugins/4284) can add its own set of environment variables, or expand on the above _build_ related flags.

The `build-environment` keyword can be used to either override the default environment variables or define new ones. Here is a basic example:

```yaml
parts:
  hello-part:
    source: gnu-hello.tar.gz
    plugin: autotools
    build-environment:
    - CFLAGS: "$CFLAGS -O3"  # add -O3 to the existing flags
    - LDFLAGS: "-L$SNAPCRAFT_STAGE/non-standard/lib"
```
The above example will override default flags and search for libraries in a non-standard path.

For a complete list of environment variables, see [Environment variables exposed by Snapcraft](/t/environment-variables-that-snapcraft-exposes/7569).