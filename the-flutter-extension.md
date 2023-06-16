.. 19166.md

.. _the-flutter-extension:

# The flutter extension

There are currently four Flutter extensions.  They each track a different [Flutter build release channel](https://github.com/flutter/flutter/wiki/Flutter-build-release-channels) to help with the creation of snaps that use the [Flutter UI toolkit](https://flutter.dev/):

- **flutter-stable** tracks Flutter's stable channel
- **flutter-beta** tracks Flutter's beta channel
- **flutter-master** tracks Flutter's master channel
- **flutter-dev** tracks Flutter's dev channel

> ⓘ The Flutter extension does not currently support [core22](base-snaps.md). Snaps using `core22` should instead use the [flutter](the-flutter-plugin.md) plugin with the [gnome](the-gnome-extension.md) extension.

Each Flutter extension uses the [gnome-3-28 extension](the-gnome-3-28-extension.md) to provide many of the components needed to build Flutter desktop applications.

Use of the [flutter plugin](the-flutter-plugin.md) is optional. The plugin drives the build process while the extension handles its dependencies.

- [Using the extensions](#the-flutter-extension-heading--how): adding the necessary keywords to your snapcraft.yaml
- [Interface connections](#the-flutter-extension-heading--plugs): which interfaces are accessible from the extension

> ℹ  Snapcraft extensions enable snap developers to easily incorporate a set of common requirements into a snap. See [Snapcraft extensions](snapcraft-extensions.md) for further details.

<h2 id='the-flutter-extension-heading--how'>Using the extensions</h2>

Each Flutter extension works with the `core18` base snap (see [Base snaps](base-snaps.md) for details). To use either extension, add `extensions: [flutter-master]` or `extensions: [flutter-dev]` to the application definition in your [snapcraft.yaml](creating-snapcraft-yaml.md) file. For instance:

```yaml
apps:
    tali:
        extensions: [flutter-master]
        command: usr/bin/tali
[...]
```

See [Flutter applications](flutter-applications.md) for a comprehensive overview of using extensions with Flutter applications.

<h2 id='the-flutter-extension-heading--plugs'>Interface connections</h2>

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

See [Adding interfaces](adding-interfaces.md) for more details.