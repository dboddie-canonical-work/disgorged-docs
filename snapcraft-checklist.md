.. 10926.md

.. _snapcraft-checklist:

# Snapcraft checklist

Before you can build a snap, you need to know a few attributes about your application.

These attributes ensure a snap can be built and, via a 3-point checklist outlined below, help with the construction of the application's *snapcraft.yaml*.

## Prerequisites

There are currently a few types of project that are unsuitable for snaps:
- libraries
- media content providers (except themes)
- applications built specifically for ARMv6
- applications that need a binary in `/snap/core18/current/{bin,usr/bin}/*`

> Due to Snapcraft's flexibility, there are exceptions to the above. These include [FFmpeg](the-ffmpeg-sdk-stage-snaps.md) and [wxWidget](the-wxwidgets-sdk-stage-snaps.md) stage snaps, and the [Hunspell dictionaries](the-hunspell-dictionaries-content-snaps.md) snap.

Before going any further, make sure your project builds and runs from a clean environment. This will help clarify any wayward dependencies or specific installation requirement that may have been forgotten in an old build tree.

## Creating a checklist

A snap's requirements reflect those of the application itself.

If you're a developer working on the application, or a technical user familiar with a project, a snap's requirements won't contain any surprises; they're what you need to build your application.

Split roughly into their relevance, and the order you should tackle each requirement, here's what you need to know:

### 1. **Language/Framework/Build system** (*mandatory*)

This is the foundation of your snap. It defines how your snap is built and is often an extension of the programming language you're using. Examples include Python applications using [PyPI](https://pypi.org/) and Go projects using [go get](https://golang.org/pkg/cmd/go/internal/get/), but also build systems like [cmake](the-cmake-plugin.md) and platforms like [Electron](electron-apps.md).

Snapcraft uses [plugins](snapcraft-plugins.md) to create the build environment, and there are plugins for many of the most popular build systems. See [Supported plugins](supported-plugins.md) for more details.

> Applications can be built using a single part with a single plugin, or from multiple parts and multiple plugins, depending on their complexity.

### 2. **Toolkits and desktop support** (*optional*)

Many applications use a toolkit, such as [Qt](https://www.qt.io/) or [GTK](https://www.gtk.org/), to provide both functionality and better system integration.

There are recipes for incorporating many popular toolkits into your snap, either by pasting pre-configured snippets into your snap's *snapcraft.yaml*, or by using a new Snapcraft feature called [Extensions](snapcraft-extensions.md).

See [Desktop app support](desktop-applications.md) for examples with toolkit and desktop integration.

### 3. **System integration** (*optional*)

Your application may have requirements of the system it's running on, and these requirements are typically satisfied by configuring one or more [interfaces](interface-management.md).

These requirements may be as simple as access to a user's [home directory](the-home-interface.md), sound [playback](the-audio-playback-interface.md) and [recording](the-audio-record-interface.md) via PulseAudio and [desktop interfaces](the-desktop-interfaces.md). But they can equally include [process management](the-process-control-interface.md) or [memory access](the-physical-memory-observe-interface.md).