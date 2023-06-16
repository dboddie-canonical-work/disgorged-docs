.. 11473.md

.. _adding-parts:

# Adding parts

When building a snap with [Snapcraft](/t/snapcraft-overview/8940), parts are used to describe your application, where its various components can be found, its build and run-time requirements, and those of its dependencies. Consequently, a snap always has one or more parts.

A part's definition within [snapcraft.yaml](/t/the-snapcraft-format/8337) is purposely flexible to allow for varied and disparate sources.

At its simplest, a part will locate a project's source code and to invoke a [plugin](/t/snapcraft-plugins/4284) to build and deploy the consequent application within your snap environment. But a part can equally be used to source and unpack a binary executable from an RPM file, or override into the correct location.

A part can also download tagged code from a remote repository, pull in dependencies, define a build order, and completely override both the *snapcraft build* and the *snapcraft stage* phases of the process.

For more details on how parts are built within the *snapcraft* environment, including build stages and the directories they use, see [Parts lifecycle](/t/parts-lifecycle/12231).

## Defining a part

The `snapcraft init` command creates the following *part* template in *snapcraft.yaml*:

```yaml
parts:
  my-part:
    # See 'snapcraft plugins'
    plugin: nil
```

A part starts with an arbitrary name, such as `my-part`, which is followed by enough [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336) to build the functionality you require.

The core of a typical part will commonly consist of the following metadata:

- **plugin**
  Used to simplify and accelerate your build on commonly used frameworks and platforms. A plugin will often add, and may require, its own additional metadata. See [Snapcraft plugins](/t/snapcraft-plugins/4284) for more details.
  Examples: `python`, `go`, `java`, `cmake`, `autotools`
- **source**
  The location of the file or files needed to build your part. It can refer to a directory tree, a compressed archive, or a revision control repository.
  Examples: `.`, `https://github.com/coderholic/pyradio.git`, `gnu-hello.tar.gz`
- **build-packages**
  A list of the packages required to build your part. Package names are those used by the build host's package manager, such as *apt* or *dnf*.
  Examples: `[pkg-config,  libncursesw5-dev, sed ]`
- **build-snaps**
  A list of the snaps required to build your part. Snap names can include [track and channel](/t/channels/551) options (`<track>/<risk>/<branch>`).
  Examples: `[go/1.16/stable,  kde-frameworks-5-core18-sdk]`
- **stage-packages**
  A list of the packages required by your part to *run*. Package names are those used by the build host's package manager, such as *apt* or *dnf*.
  Examples: `[gnome-themes-standard, libncursesw5, dbus]`
- **stage-snaps**
  A list of the snaps required by your part to *run*. As with _build-snaps_, you can optionally add the [track and channel](/t/channels/551) of the snaps you wish to include.
  Examples: `[ffmpeg-sdk-gplv3, codium/latest/stable]`

As per the [YAML specification](https://yaml.org/spec/), the members of a list in *snapcraft.yaml* can be formatted in either of the following ways:

```yaml
build-packages: [g++, make, git, sed]

build-packages:
- g++
- make
- git
- sed
```

For help on working out which packages you need for both building and staging your snap, take a look at [Build and staging dependencies](/t/build-and-staging-dependencies/11451), and see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336) for a complete list of supported *parts* keywords.

Parts can also be sourced from shell scripts outside of the _snapcraft.yaml_. See [Scriptlets](/t/scriptlets/4892) for details.