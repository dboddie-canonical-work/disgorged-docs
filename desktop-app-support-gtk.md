.. 6834.md

.. _desktop-app-support-gtk:

# Desktop App Support - GTK

## Snapping GTK applications

Graphical applications which use [GTK](https://www.gtk.org/) require additional libraries, environment configuration and interfaces to function correctly inside a snap. Follow the instructions for the version of GTK your application uses.

* The [gnome-3-28 extension](the-gnome-3-28-extension.md) is the easiest way to support **GTK 3** applications. See [GTK 3 applications](gtk3-applications.md) for a complete tutorial on how to use this extension.
* If your application uses **GTK+ 2**, please see gtk2-applications.md

## [legacy] Snaps that don't use `base`

The `gnome-3-28` extension only works with snaps that use `base: core18`. There are some tools that can help you if your snap doesn't use `base: core18`, however, it is preferred to upgrade your snap to use `base: core18`.

* 13506.md