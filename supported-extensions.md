.. 20521.md

.. _supported-extensions:

# Supported extensions

Snapcraft extensions enable snap developers to easily incorporate a set of common requirements into a snap. For more information on how to use extensions, see [Snapcraft extensions](snapcraft-extensions.md).

The following extensions are available in the latest version of [Snapcraft](snapcraft-overview.md).

| Extension name | Description | [Supported base](base-snaps.md) |
|--|--|--|--|
| [flutter-stable](the-flutter-extension.md) | Create snaps that  track the _stable_ channel of the [Flutter UI toolkit](https://flutter.dev/)| core18 |
| [flutter-beta](the-flutter-extension.md) | Create snaps that  track the _beta_ channel of the [Flutter UI toolkit](https://flutter.dev/)| core18 |
| [flutter-dev](the-flutter-extension.md) | Create snaps that  track the _dev_ channel of the [Flutter UI toolkit](https://flutter.dev/)| core18 |
| [flutter-master](the-flutter-extension.md) | Create snaps that  track the _master_ channel of the [Flutter UI toolkit](https://flutter.dev/)  | core18 |
| [gnome](the-gnome-extension.md) | Create snaps that integrate with GNOME and GTK. Also useful for general desktop applications. | core22 |
| [gnome-3-38](the-gnome-3-38-extension.md) | This older version of the `gnome` extension supports GTK 3.38 and core20 | core20 |
| [gnome-3-34](the-gnome-3-34-extension.md) |  This older version of the `gnome` extension supports GTK 3.34 and core18 | core18 |
| [gnome-3-28](the-gnome-3-28-extension.md) | This older version of the `gnome` extension supports GTK 3.28 and core18  | core18 |
| [kde-neon](the-kde-neon-extension.md) | Create snaps of desktop applications that use Qt5 and/or [KDE Frameworks](https://kde.org/products/frameworks/) | core18</br>  core20</br>core22|
| [ros2-foxy](the-ros2-foxy-extension.md) | This extension helps you snap ROS 2 applications for the [Foxy Fitzroy](https://index.ros.org/doc/ros2/Releases/Release-Foxy-Fitzroy/) distribution _(experimental)_     | core20 |
| [ros2-humble](the-ros-2-humble-extension.md) | This extension helps you snap ROS 2 applications for the [Humble Hawksbill](https://docs.ros.org/en/foxy/Releases/Release-Humble-Hawksbill.html) distribution _(experimental)_     | core22 |
| [ros1-noetic](the-ros-1-noetic-extension.md) | This extension helps you snap ROS 1 applications for the [Noetic Ninjemys](https://wiki.ros.org/noetic) distribution _(experimental)_  | core20 |

The _snapcraft extensions_ command lists which extensions are supported by the installed version of snapcraft.