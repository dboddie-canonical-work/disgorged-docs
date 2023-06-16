.. 20521.md

.. \_supported-extensions:

Supported extensions
====================

Snapcraft extensions enable snap developers to easily incorporate a set of common requirements into a snap. For more information on how to use extensions, see `Snapcraft extensions <snapcraft-extensions.md>`__.

The following extensions are available in the latest version of `Snapcraft <snapcraft-overview.md>`__.

+-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+-----------------+
| Extension name                                  | Description                                                                                                                                                                       | `Supported base <base-snaps.md>`__ |                 |
+=================================================+===================================================================================================================================================================================+====================================+=================+
| `flutter-stable <the-flutter-extension.md>`__   | Create snaps that track the *stable* channel of the `Flutter UI toolkit <https://flutter.dev/>`__                                                                                 | core18                             |                 |
+-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+-----------------+
| `flutter-beta <the-flutter-extension.md>`__     | Create snaps that track the *beta* channel of the `Flutter UI toolkit <https://flutter.dev/>`__                                                                                   | core18                             |                 |
+-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+-----------------+
| `flutter-dev <the-flutter-extension.md>`__      | Create snaps that track the *dev* channel of the `Flutter UI toolkit <https://flutter.dev/>`__                                                                                    | core18                             |                 |
+-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+-----------------+
| `flutter-master <the-flutter-extension.md>`__   | Create snaps that track the *master* channel of the `Flutter UI toolkit <https://flutter.dev/>`__                                                                                 | core18                             |                 |
+-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+-----------------+
| `gnome <the-gnome-extension.md>`__              | Create snaps that integrate with GNOME and GTK. Also useful for general desktop applications.                                                                                     | core22                             |                 |
+-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+-----------------+
| `gnome-3-38 <the-gnome-3-38-extension.md>`__    | This older version of the ``gnome`` extension supports GTK 3.38 and core20                                                                                                        | core20                             |                 |
+-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+-----------------+
| `gnome-3-34 <the-gnome-3-34-extension.md>`__    | This older version of the ``gnome`` extension supports GTK 3.34 and core18                                                                                                        | core18                             |                 |
+-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+-----------------+
| `gnome-3-28 <the-gnome-3-28-extension.md>`__    | This older version of the ``gnome`` extension supports GTK 3.28 and core18                                                                                                        | core18                             |                 |
+-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+-----------------+
| `kde-neon <the-kde-neon-extension.md>`__        | Create snaps of desktop applications that use Qt5 and/or `KDE Frameworks <https://kde.org/products/frameworks/>`__                                                                | core18 core20core22                |                 |
+-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+-----------------+
| `ros2-foxy <the-ros2-foxy-extension.md>`__      | This extension helps you snap ROS 2 applications for the `Foxy Fitzroy <https://index.ros.org/doc/ros2/Releases/Release-Foxy-Fitzroy/>`__ distribution *(experimental)*           | core20                             |                 |
+-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+-----------------+
| `ros2-humble <the-ros-2-humble-extension.md>`__ | This extension helps you snap ROS 2 applications for the `Humble Hawksbill <https://docs.ros.org/en/foxy/Releases/Release-Humble-Hawksbill.html>`__ distribution *(experimental)* | core22                             |                 |
+-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+-----------------+
| `ros1-noetic <the-ros-1-noetic-extension.md>`__ | This extension helps you snap ROS 1 applications for the `Noetic Ninjemys <https://wiki.ros.org/noetic>`__ distribution *(experimental)*                                          | core20                             |                 |
+-------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------+-----------------+

The *snapcraft extensions* command lists which extensions are supported by the installed version of snapcraft.