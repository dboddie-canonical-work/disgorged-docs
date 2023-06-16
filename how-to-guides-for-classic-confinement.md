.. 34416.md

.. _how-to-guides-for-classic-confinement:

# How to guides for classic confinement

[Classic confinement](/t/6233) is used for snaps that need to access system resources outside the strict confinement usually used.

When a snap uses classic confinement, it relies on libraries on the user's system instead of those provided by a base snap. Care must be taken to ensure that the application in the snap is linked against the correct libraries.

These guides show how classic confinement can be enabled for different types of projects, addressing any linking issues:

* [Set up classic confinement for an autotools project](/t/34099)
* [Set up classic confinement for a Python project](/t/34179)
* [Set up classic confinement for a Makefile project](/t/34097)
* [Set up classic confinement for a CMake project](/t/34627)