.. 13485.md

.. _the-gnome-3-28-extension:

# The gnome-3-28 extension

This extension helps you snap desktop applications that use GTK 3, GNOME 3.28 and/or GLib.

## How to use it

Add `extensions: [ gnome-3-28 ]` to the application definition in your `snapcraft.yaml` file. See [GTK3 applications](gtk3-applications.md) for a complete tutorial on how to use this extension.

```yaml
apps:
  foliate:
    command: usr/bin/com.github.johnfactotum.Foliate
    extensions: [gnome-3-28]
    ...
```

## When to use it

Although this extensions adds support for the GTK 3 runtime, it also includes base desktop technologies such as GLib and cursor themes, so it is useful to almost any desktop application which does not have a more specialized extension available.

Some examples:

* [GTK3 applications](gtk3-applications.md)
* [Java Swing applications](java-applications.md), except when they use [GTK+ 2 integration](gtk2-applications.md).
* Games

This extension will _not_ work for [GTK+ 2 applications](gtk2-applications.md) and 32-bit applications.

See [Desktop Applications](desktop-applications.md) for more information on how to snap a desktop application.

## What it does

* It ensures the GTK3 and GNOME libraries are available to all parts at build and run time.
* It initialises GTK3 and the desktop environment before your application starts so functionality like fonts, themes and a11y works correctly.

To do this, it connects each application to the following content snaps at run time.

- [`gtk-common-themes`](https://snapcraft.io/gtk-common-themes) for common GTK, icon, cursor and sound themes.
- [`gnome-3-28-1804`](https://snapcraft.io/gnome-3-28-1804) for the GNOME runtime libraries and utilities corresponding to 3.28.

It also configures each application entry with these additional plugs:

- [desktop](the-desktop-interface.md)
- [desktop-legacy](the-desktop-interface.md)
- [wayland](the-wayland-interface.md)
- [x11](the-x11-interface.md)

> ℹ  Snapcraft extensions enable snap developers to easily incorporate a set of common requirements into a snap. See [Snapcraft extensions](snapcraft-extensions.md) for further details.