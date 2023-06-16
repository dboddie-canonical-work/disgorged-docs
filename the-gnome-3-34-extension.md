.. 18485.md

.. _the-gnome-3-34-extension:

# The gnome-3-34 extension

The _gnome-3-34_ extension helps with the creation of snaps that use GTK 3, GNOME 3.34, and/or GLib. It's an updated version of the [gnome-3-28 extension](/t/the-gnome-3-28-extension/13485) and depends on the `core18` [base snap](/t/base-snaps/11198), built from [Ubuntu 18.04 LTS ](http://releases.ubuntu.com/18.04/). The more recent [gnome-3-38 extension](/t/the-gnome-3-38-extension/22923) is built only for `core20`.

This extension provides many of the components needed for general desktop applications making it useful for a broader set of applications outside of those tailored for the GNOME desktop.

- [How to use it](#heading--how): adding the necessary keywords to your snapcraft.yaml
- [Interface connections](#heading--plugs): which interfaces are accessible from the extension
- [Included packages](#heading--packages): a list of the packages the extension is build from and provides
- [Environment variables](#heading--environment): variables used during build and snap runntime
- [Layout set](#heading--layouts): layouts used by this extension to access files on the host

> ℹ  Snapcraft extensions enable snap developers to easily incorporate a set of common requirements into a snap. See [Snapcraft extensions](/t/snapcraft-extensions/13486) for further details.

<h2 id='heading--how'>How to use it</h2>

This extension currently only works with the `core18` base snap (see [Base snaps](/t/base-snaps/11198) for details). To use it, add `extensions: [gnome-3-34]` to the application definition in your [snapcraft.yaml](/t/creating-snapcraft-yaml/11666) file. For instance:

```yaml
apps:
    tali:
        extensions: [gnome-3-34]
        command: usr/bin/tali
[...]
```

See [GTK3 applications](/t/gtk3-applications/13483) for a comprehensive overview of using extensions with GNOME applications.

<h2 id='heading--plugs'>Interface connections</h2>

The following plugs are provided by the extension and implicitly included in your snapcraft.yaml:

```yaml
plugs:
    gtk-3-themes:
        interface: content
        target: $SNAP/data-dir/themes
        default-provider: gtk-common-themes
    icon-themes:
            interface: content
            target: $SNAP/data-dir/icons
            default-provider: gtk-common-themes
    sound-themes:
            interface: content
            target: $SNAP/data-dir/sounds
            default-provider: gtk-common-themes
    platform_snap:
            interface: content
            target: $SNAP/gnome-platform
            default-provider: gnome-3-34-1804
```

Your app may still  need additional plugs, but you can expect the following plugs to be automatically available to your apps as well:

```
plugs: [ desktop, desktop-legacy, gsettings, wayland, x11 ]
```

See [Adding interfaces](/t/adding-interfaces/13123) for more details.

<h2 id='heading--packages'>Included packages</h2>

The GNOME extension is derived from two separate snaps; a [build snap](https://gitlab.gnome.org/Community/Ubuntu/gnome-sdk/blob/gnome-3-34-1804-sdk/snapcraft.yaml) and a [platform snap](https://gitlab.gnome.org/Community/Ubuntu/gnome-sdk/blob/gnome-3-34-1804/snapcraft.yaml).

The _build snap_ builds 35 libraries from source that are commonly used across GNOME applications. Examples include glib, gtk, and gnome-desktop. These are built to provide newer versions of these packages that exist in the core18 base snap (a subset of the Ubuntu 18.04 archive).

It is common for GNOME applications to release a gnome-3-34 branch of their project when the 3.34 version of GNOME is released (or shortly thereafter). Keeping this in mind, the build snap looks for this first to provide access to various GNOME libraries on their gnome-3-34 branch, to distribute the latest stable version that corresponds to the GNOME 3.34 release.

The _platform snap_ takes the build snap and makes all of those libraries available to your snap at build time without needing to include the pieces of the build snap that are unnecessary at runtime (like compilers) in your final snap.

The libraries built in the gnome-3-34-1804-sdk build snap are:
[details=gnome-3-34-1804-sdk libraries]
-   libtool
-   libffi
-   glib (2.62)
-   pixman (0.38.4)
-   cairo (1.16.0)
-   gobject-introspection (gnome-3-34 branch)
-   vala (0.46)
-   gee (0.20.2)
-   atk (gnome-3-34 branch)
-   at-spi2-core (2.34.0)
-   at-spi2-atk (2.34.1)
-   fribidi (1.0.7)
-   harfbuzz (2.6.2)
-   pango (1.44.6-2)
-   librsvg (2.44)
-   gdk-pixbuf (2.38)
-   epoxy (1.5.3)
-   json-glib (1.4)
-   libpsl (0.21.0)
-   libsoup (2.68.2)
-   librest (0.7)
-   gtk (3.24.10)
-   gtk-locales
-   mm-common (1.0.0)
-   glibmm (2.62.0)
-   cairomm (1.12.2)
-   pangomm (2.42.0)
-   atkmm (2.28.0)
-   gtkmm (3.24.2)
-   gtksourceview (4.4.0)
-   libdazzle (3.34)
-   libcanberra
-   gsettings-desktop-schemas (gnome-3-34 branch)
-   gnome-desktop (gnome-3-34 branch)
-   cogl (1.22)
-   clutter
-   clutter-gtk (1.8.4)
-   libpeas (1.22.0)
-   pycairo (1.18.1)
-   pygobject (3.34)
-   libhandy (libhandy-0-0 branch)
[/details]

There are also several packages included from the Ubuntu 18.04 apt repository:

[details=additional packages]
-   gcc
-   pkg-config
-   libpcre3-dev
-   zlib1g-dev
-   libmount-dev
-   libxml2-dev
-   libsqlite3-dev
-   libbrotli-dev
-   libthai-dev
-   libfontconfig1-dev
-   libxrender-dev
-   libxft-dev
-   libxcb-shm0-dev
-   libxcb-render0-dev
-   libxext-dev
-   libxi-dev
-   libxrandr-dev
-   libxcursor-dev
-   libxcomposite-dev
-   libxdamage-dev
-   libxinerama-dev
-   libwayland-dev
-   wayland-protocols
-   libxkbcommon-dev
-   libgl1-mesa-dev
-   libegl1-mesa-dev
-   libdbus-1-dev
-   libxtst-dev
-   gettext
-   shared-mime-info
-   libwebkit2gtk-4.0-dev
-   libgcr-3-dev
-   libnotify-dev
-   libsecret-1-dev
-   itstool
-   libudev-dev
-   libseccomp-dev
-   libjpeg-dev
-   liblcms2-dev
-   libgspell-1-dev
-   python3-minimal
-   libxml2-utils
-   libgtksourceview-3.0-dev
-   libtdb1
-   libvorbisfile3
-   libegl-mesa0
[/details]

<h2 id='heading--environment'>Environment variables</h2>

In addition to using the build and platform snaps, the _gnome-3-34 extension_ also sets a collection of environment variables, links, default plugs for the app to use, and a default build-environment for each part in your snap to use.

### Build variables

The following "build-environment" section is made available to each part built in your snap.

If you define other build-environment variables, then those will get added to these and the set is used. If you define another value for one of these variables, then the value you've defined will be used instead of the value defined within the extension.

```yaml
build-environment:
   - PATH: /snap/gnome-3-34-1804-sdk/current/usr/bin:$PATH
   - XDG_DATA_DIRS: /snap/gnome-3-34-1804-sdk/current/usr/share:/usr/share:$XDG_DATA_DIRS
   - LD_LIBRARY_PATH:/snap/gnome-3-34-1804-sdk/current/lib/$SNAPCRAFT_ARCH_TRIPLET:/snap/gnome-3-34-1804-sdk/current/usr/lib/$SNAPCRAFT_ARCH_TRIPLET:/snap/gnome-3-34-1804-sdk/current/usr/lib:/snap/gnome-3-34-1804-sdk/current/usr/lib/vala-current:$LD_LIBRARY_PATH
   - PKG_CONFIG_PATH: /snap/gnome-3-34-1804-sdk/current/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/pkgconfig:/snap/gnome-3-34-1804-sdk/current/usr/lib/pkgconfig:/snap/gnome-3-34-1804-sdk/current/usr/share/pkgconfig:$PKG_CONFIG_PATH
   - GETTEXTDATADIRS:/snap/gnome-3-34-1804-sdk/current/usr/share/gettext-current:$GETTEXTDATADIRS
   - GDK_PIXBUF_MODULE_FILE: /snap/gnome-3-34-1804-sdk/current/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/gdk-pixbuf-current/loaders.cache
```

### Runtime variables

The following environment is set when your application is run:

```yaml
 environment:
   - SNAP_DESKTOP_RUNTIME: $SNAP/gnome-platform
   - GTK_USE_PORTALS: 1
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