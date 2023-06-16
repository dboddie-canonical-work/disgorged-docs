.. 13034.md

.. _desktop-applications:

# Desktop applications

Distributing a Desktop GUI application for Linux while reaching the widest possible audience is complicated. Typically, the user has to make sure the correct version of the GUI toolkit is installed and configured. When a Linux distribution changes the delivered GUI toolkits, this can be problematic for applications.

Snaps solve these problems and ensure the correct toolkit libraries are shipped alongside the application at all times.

## Getting Started

Read the documentation of the GUI toolkit your application uses in order to get started!

| Common GUI Toolkits | Technologies |
|-------------------------------|-------------------|
| [GTK 3](https://forum.snapcraft.io/t/gtk3-applications/13483) |  [OpenGL/GPU support](/t/adding-opengl-gpu-support-to-a-snap/6273) |
| [GTK+ 2](/t/gtk2-applications/13508) | [Desktop Launchers / Menu entries](https://forum.snapcraft.io/t/desktop-files-for-menu-integration/13115) |
| [Qt 5 and KDE Frameworks](/t/qt5-and-kde-frameworks-applications/13753) | [XDG desktop portals](/t/xdg-desktop-portals/17331) |
| [Java Swing](/t/java-applications/7819) | [AppStream metadata support](/t/using-external-metadata/4642) |
| [Electron](/t/electron-apps/6748) |  [chromium-ffmpeg in third-party browser snaps](https://forum.snapcraft.io/t/using-chromium-ffmpeg-in-third-party-browser-snaps/6545)|
| [Flutter](https://forum.snapcraft.io/t/flutter-applications/18768) | [The desktop interfaces](/t/the-desktop-interfaces/2042) |

<!--- [wxWidgets](/t/the-wxwidgets-sdk-stage-snaps/10877) (not including this since it's an unmaintained community project)-->

## Refining

* [Reduce the size of your snap](/t/reducing-the-size-of-desktop-snaps/17280). This will also speed up how quickly your snap starts!
* [Switch the compression to `lzo`](/t/snapcraft-top-level-metadata/8334#heading--compression) to make your application start up even quicker.
* Make sure your application has a [logo in the snap store](/t/store-listing-and-branding/16397#heading--logo-icon) and [screenshots](/t/store-listing-and-branding/16397#heading--screenshots).
* Include a link to your contact page or bugtracker in the [store metadata](https://forum.snapcraft.io/t/store-listing-and-branding/16397#heading--metadata).

## Further Information

Compared to CLI apps, desktop apps typically require three additional features.

1. Access to the host system to play sound, create notifications, display a window, etc.
1. Access to a GUI toolkit such as GTK or Qt.
1. Initialisation of desktop-specific functionality such as fonts, themes and the [XDG](https://www.freedesktop.org) environment.


Since snap apps are completely sandboxed by default, they cannot play sound, create notifications, or access the X server to display itself. However, it's easy to make this possible by using the **[desktop interfaces](/t/the-desktop-interfaces/2042)**. These allow you to "poke holes" in the sandbox, to give your application selected access to the host system.

The sandbox also means that your app cannot use the GUI toolkits of the host system. The snap either has to include the toolkit in the snap itself, or it needs to connect to a snap that provides these toolkits. Many toolkits and general desktop features such as fonts and themes also require initialization before the application can start. The extensions make this as easy as possible. They provide parts to bundle or access common GUI toolkits in your snap and a `desktop-launch` script which does the required initialization for you.

## Legacy

These methods are not recommended anymore but might be useful as reference.

* [Qt 5 support using the `desktop-helpers`](/t/desktop-app-support-qt5/11703)
* [`snapcraft-desktop-helpers`](https://github.com/ubuntu/snapcraft-desktop-helpers/) provided useful parts and launchers for desktop snaps, but these are deprecated in favor of the `gnome-*` and `kde-neon` extensions.