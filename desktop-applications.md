.. 13034.md

.. _desktop-applications:

# Desktop applications

Distributing a Desktop GUI application for Linux while reaching the widest possible audience is complicated. Typically, the user has to make sure the correct version of the GUI toolkit is installed and configured. When a Linux distribution changes the delivered GUI toolkits, this can be problematic for applications.

Snaps solve these problems and ensure the correct toolkit libraries are shipped alongside the application at all times.

## Getting Started

Read the documentation of the GUI toolkit your application uses in order to get started!

| Common GUI Toolkits | Technologies |
|-------------------------------|-------------------|
| [GTK 3](gtk3-applications.md) |  [OpenGL/GPU support](adding-opengl-gpu-support-to-a-snap.md) |
| [GTK+ 2](gtk2-applications.md) | [Desktop Launchers / Menu entries](desktop-files-for-menu-integration.md) |
| [Qt 5 and KDE Frameworks](qt5-and-kde-frameworks-applications.md) | [XDG desktop portals](xdg-desktop-portals.md) |
| [Java Swing](java-applications.md) | [AppStream metadata support](using-external-metadata.md) |
| [Electron](electron-apps.md) |  [chromium-ffmpeg in third-party browser snaps](using-chromium-ffmpeg-in-third-party-browser-snaps.md)|
| [Flutter](flutter-applications.md) | [The desktop interfaces](the-desktop-interfaces.md) |

<!--- [wxWidgets](the-wxwidgets-sdk-stage-snaps.md) (not including this since it's an unmaintained community project)-->

## Refining

* [Reduce the size of your snap](reducing-the-size-of-desktop-snaps.md). This will also speed up how quickly your snap starts!
* [Switch the compression to `lzo`](snapcraft-top-level-metadata.md#heading--compression) to make your application start up even quicker.
* Make sure your application has a [logo in the snap store](https://snapcraft.io/docs/store-listing-and-branding#heading--logo-icon) and [screenshots](https://snapcraft.io/docs/store-listing-and-branding#heading--screenshots).
* Include a link to your contact page or bugtracker in the [store metadata](https://snapcraft.io/docs/store-listing-and-branding#heading--metadata).

## Further Information

Compared to CLI apps, desktop apps typically require three additional features.

1. Access to the host system to play sound, create notifications, display a window, etc.
1. Access to a GUI toolkit such as GTK or Qt.
1. Initialisation of desktop-specific functionality such as fonts, themes and the [XDG](https://www.freedesktop.org) environment.


Since snap apps are completely sandboxed by default, they cannot play sound, create notifications, or access the X server to display itself. However, it's easy to make this possible by using the **[desktop interfaces](the-desktop-interfaces.md)**. These allow you to "poke holes" in the sandbox, to give your application selected access to the host system.

The sandbox also means that your app cannot use the GUI toolkits of the host system. The snap either has to include the toolkit in the snap itself, or it needs to connect to a snap that provides these toolkits. Many toolkits and general desktop features such as fonts and themes also require initialization before the application can start. The extensions make this as easy as possible. They provide parts to bundle or access common GUI toolkits in your snap and a `desktop-launch` script which does the required initialization for you.

## Legacy

These methods are not recommended anymore but might be useful as reference.

* [Qt 5 support using the `desktop-helpers`](deprecated-desktop-app-support-qt5.md)
* [`snapcraft-desktop-helpers`](https://github.com/ubuntu/snapcraft-desktop-helpers/) provided useful parts and launchers for desktop snaps, but these are deprecated in favor of the `gnome-*` and `kde-neon` extensions.