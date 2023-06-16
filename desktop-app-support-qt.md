.. 6833.md

.. _desktop-app-support-qt:

# Desktop App support - Qt

## Snapping Qt applications

Use the following guides to create a new snap for a graphical application which uses [Qt](https://www.qt.io/). These guides use the stable Qt versions which are shipped with Ubuntu 16.04 and 18.04 LTS and are recommended for most applications and new snaps.

* [Desktop App support - Qt5](deprecated-desktop-app-support-qt5.md)
* [Desktop App support - Qt4](desktop-app-support-qt4.md)

## [legacy] snaps that don't use `base`

If you have an existing snap that does not use the [base](https://snapcraft.io/docs/base-snaps) functionality, please use the following guide.

* [[Legacy] Desktop App support - Qt for snaps without bases](desktop-app-support-qt-for-snaps-without-bases.md)

## Snapping KDE applications

The KDE community has developed tools to help them snap the [KDE applications](https://kde.org/applications/). These applications require the latest version of Qt and the [KDE frameworks](https://kde.org/products/frameworks/) which are not provided by Ubuntu LTS. Use the following guide to snap a KDE application using the latest libraries.

* [Desktop App support - KDE applications](https://community.kde.org/Guidelines_and_HOWTOs/Snap)

*Note: this method is not recommended for regular Qt applications, as it is specifically tailored towards KDE applications.*