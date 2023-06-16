.. 22923.md

.. _the-gnome-3-38-extension:

# The gnome-3-38 extension

The _gnome-3-38_ extension helps with the creation of snaps that use GTK 3, GNOME 3.38, and/or GLib. It's an updated version of the [gnome-3-34 extension](/t/the-gnome-3-34-extension/18485) that works specifically with the `core20` [base snap](/t/base-snaps/11198) built from [Ubuntu 20.04 LTS](http://releases.ubuntu.com/20.04/). Previous Gnome extensions were built to use `core18`, based on [Ubuntu 18.04 LTS ](http://releases.ubuntu.com/18.04/).

[note type="caution" status="Experimental support"]

The _gnome-3-38_ extension is considered experimental and requires the `--enable-experimental-extensions` argument added to the _snapcraft_ command for versions of Snapcraft lesser than 4.6.
[/note]

This extension provides many of the components needed for general desktop applications making it useful for a broader set of applications outside of those tailored for the GNOME desktop.

- [How to use it](#heading--how): adding the necessary keywords to your snapcraft.yaml
- [Interface connections](#heading--plugs): which interfaces are accessible from the extension
- [Included packages](#heading--packages): a list of the packages the extension is build from and provides
- [Environment variables](#heading--environment): variables used during build and snap runntime
- [Layout set](#heading--layouts): layouts used by this extension to access files on the host

> ℹ  Snapcraft extensions enable snap developers to easily incorporate a set of common requirements into a snap. See [Snapcraft extensions](/t/snapcraft-extensions/13486) for further details.

<h2 id='heading--how'>How to use it</h2>

This extension currently only works with the `core20` base snap (see [Base snaps](/t/base-snaps/11198) for details). To use it, add `extensions: [gnome-3-38]` to the application definition in your [snapcraft.yaml](/t/creating-snapcraft-yaml/11666) file. For instance:

```yaml
apps:
    tali:
        extensions: [gnome-3-38]
        command: usr/bin/tali
[...]
```

See [GTK3 applications](/t/gtk3-applications/13483) for a comprehensive overview of using extensions with GNOME applications.

<h2 id='heading--plugs'>Interface connections</h2>

The following plugs are provided by the extension and implicitly included in your snapcraft.yaml:

```yaml
plugs:
  gnome-3-38-2004:
    default-provider: gnome-3-38-2004
    interface: content
    target: $SNAP/gnome-platform
  gtk-3-themes:
    default-provider: gtk-common-themes
    interface: content
    target: $SNAP/data-dir/themes
  icon-themes:
    default-provider: gtk-common-themes
    interface: content
    target: $SNAP/data-dir/icons
  sound-themes:
    default-provider: gtk-common-themes
    interface: content
    target: $SNAP/data-dir/sounds
```

Your app may still  need additional plugs, but you can expect the following plugs to be automatically available to your apps as well:

```
plugs: [ desktop, desktop-legacy, gsettings, opengl,wayland, x11 ]
```

See [Adding interfaces](/t/adding-interfaces/13123) for more details.

<h2 id='heading--packages'>Included packages</h2>

The GNOME extension is derived from two separate snaps; a [build snap](https://github.com/ubuntu/gnome-sdk/blob/gnome-3-38-2004-sdk/snapcraft.yaml) and a [platform snap](https://github.com/ubuntu/gnome-sdk/blob/gnome-3-38-2004/snapcraft.yaml).

The **build snap** builds compiles libraries from source that are commonly used across GNOME applications. Examples include glib, gtk, and gnome-desktop. These are built to provide newer versions of these packages that exist in the core20 base snap (a subset of the Ubuntu 20.04 archive).

It is common for GNOME applications to release a gnome-3-38 branch of their project when the 3.38 version of GNOME is released (or shortly thereafter). Keeping this in mind, the build snap looks for this first to provide access to various GNOME libraries on their gnome-3-38 branch, to distribute the latest stable version that corresponds to the GNOME 3.38 release.

The **platform snap** takes the build snap and makes all of those libraries available to your snap at build time without needing to include the pieces of the build snap that are unnecessary at runtime (like compilers) in your final snap.

<h2 id='heading--environment'>Environment variables</h2>

In addition to using the build and platform snaps, the _gnome-3-38 extension_ also sets a collection of environment variables, links, default plugs for the app to use, and a default build-environment for each part in your snap to use.

### Build variables

The following "build-environment" section is made available to each part built in your snap.

If you define other build-environment variables, then those will get added to these and the set is used. If you define another value for one of these variables, then the value you've defined will be used instead of the value defined within the extension.

```yaml
build-environment:
    - PATH: /snap/gnome-3-38-2004-sdk/current/usr/bin:$PATH
    - XDG_DATA_DIRS: $SNAPCRAFT_STAGE/usr/share:/snap/gnome-3-38-2004-sdk/current/usr/share:/usr/share:$XDG_DATA_DIRS
    - LD_LIBRARY_PATH: /snap/gnome-3-38-2004-sdk/current/lib/$SNAPCRAFT_ARCH_TRIPLET:/snap/gnome-3-38-2004-sdk/current/usr/lib/$SNAPCRAFT_ARCH_TRIPLET:/snap/gnome-3-38-2004-sdk/current/usr/lib:/snap/gnome-3-38-2004-sdk/current/usr/lib/vala-current:/snap/gnome-3-38-2004-sdk/current/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/pulseaudio${LD_LIBRARY_PATH:+:$LD_LIBRARY_PATH}
    - PKG_CONFIG_PATH: /snap/gnome-3-38-2004-sdk/current/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/pkgconfig:/snap/gnome-3-38-2004-sdk/current/usr/lib/pkgconfig:/snap/gnome-3-38-2004-sdk/current/usr/share/pkgconfig:$PKG_CONFIG_PATH
    - GETTEXTDATADIRS: /snap/gnome-3-38-2004-sdk/current/usr/share/gettext-current:$GETTEXTDATADIRS
    - GDK_PIXBUF_MODULE_FILE: /snap/gnome-3-38-2004-sdk/current/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/gdk-pixbuf-current/loaders.cache
    - ACLOCAL_PATH: /snap/gnome-3-38-2004-sdk/current/usr/share/aclocal${ACLOCAL_PATH:+:$ACLOCAL_PATH}
    - PYTHONPATH: /snap/gnome-3-38-2004-sdk/current/usr/lib/python3.8:/snap/gnome-3-38-2004-sdk/current/usr/lib/python3/dist-packages${PYTHONPATH:+:$PYTHONPATH}
```

### Runtime variables

The following environment is set when your application is run:

```yaml
environment:
  GTK_USE_PORTAL: '1'
  SNAP_DESKTOP_RUNTIME: $SNAP/gnome-platform
```

<h2 id='heading--layouts'>Layouts set</h2>

The host's gjs, webkit2gtk-4.0, and iso-codes are used so they don't need to be packaged as part of the snap (would greatly inflate the size).

```yaml
layout:
  /usr/lib/$SNAPCRAFT_ARCH_TRIPLET/webkit2gtk-4.0:
    bind: $SNAP/gnome-platform/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/webkit2gtk-4.0
  /usr/share/xml/iso-codes:
    bind: $SNAP/gnome-platform/usr/share/xml/iso-codes
```

See [Snap layouts](/t/snap-layouts/7207) for further details.