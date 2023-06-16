.. 19166.md

.. _the-flutter-extension:

# The flutter extension

There are currently four Flutter extensions.  They each track a different [Flutter build release channel](https://github.com/flutter/flutter/wiki/Flutter-build-release-channels) to help with the creation of snaps that use the [Flutter UI toolkit](https://flutter.dev/):

- **flutter-stable** tracks Flutter's stable channel
- **flutter-beta** tracks Flutter's beta channel
- **flutter-master** tracks Flutter's master channel
- **flutter-dev** tracks Flutter's dev channel

> ⓘ The Flutter extension does not currently support [core22](/t/base-snaps/11198). Snaps using `core22` should instead use the [flutter](/t/the-flutter-plugin/18746) plugin with the [gnome](/t/the-gnome-extension/31449) extension.

Each Flutter extension uses the [gnome-3-28 extension](/t/the-gnome-3-28-extension/13485) to provide many of the components needed to build Flutter desktop applications.

Use of the [flutter plugin](/t/the-flutter-plugin/18746) is optional. The plugin drives the build process while the extension handles its dependencies.

- [Using the extensions](#heading--how): adding the necessary keywords to your snapcraft.yaml
- [Interface connections](#heading--plugs): which interfaces are accessible from the extension

> ℹ  Snapcraft extensions enable snap developers to easily incorporate a set of common requirements into a snap. See [Snapcraft extensions](/t/snapcraft-extensions/13486) for further details.

<h2 id='heading--how'>Using the extensions</h2>

Each Flutter extension works with the `core18` base snap (see [Base snaps](/t/base-snaps/11198) for details). To use either extension, add `extensions: [flutter-master]` or `extensions: [flutter-dev]` to the application definition in your [snapcraft.yaml](/t/creating-snapcraft-yaml/11666) file. For instance:

```yaml
apps:
    tali:
        extensions: [flutter-master]
        command: usr/bin/tali
[...]
```

See [Flutter applications](/t/flutter-applications/18768) for a comprehensive overview of using extensions with Flutter applications.

<h2 id='heading--plugs'>Interface connections</h2>

The following plugs are provided by either extension and implicitly included in your snapcraft.yaml:


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
```

Your app may still need additional plugs, but you can expect the following plugs to be automatically available to your apps as well:

```
plugs: [ desktop, desktop-legacy, gsettings, opengl, wayland, x11 ]
```

See [Adding interfaces](/t/adding-interfaces/13123) for more details.