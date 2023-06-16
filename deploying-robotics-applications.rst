.. 29187.md

.. _deploying-robotics-applications:

Deploying robotics applications
===============================

Improved robotics software management
-------------------------------------

When deploying robotics devices, you encounter several barriers to package, deploy, and maintain your software stack. Robotics software should benefit from a controlled and stable environment, with the same portability and reliability as any other software application. Having a production-grade update infrastructure is mandatory to stay up to date on bug fixes, new releases, and security fixes.

But developing this infrastructure can be difficult and distract you from your business goals. It also comes with overhead costs and long-term maintenance commitments.

-  Deploying software on your robots should be easy, even if your software relies on hundreds of dependencies and your robots are in different locations.

Snaps are a tailored solution for robotics software management
--------------------------------------------------------------

`Snaps <https://snapcraft.io/docs>`__ are the perfect solution for all of these challenges. Snaps are containers that bundle an application and all its dependencies, offering roboticists: \* **Containerised solution**: A containerised solution: Snaps bundle all your dependencies and assets in one package, making your application installable on dozens of Linux distributions and across distro versions. You won’t even have to install anything else on your robots’ operating system, no dependencies, not even `ROS <https://ubuntu.com/robotics/what-is-ros>`__ if you are using it. \* **Strict confinement**: Snaps are designed to be `secure and isolated <https://snapcraft.io/docs/snap-confinement>`__ from the underlying system and other applications, with `dedicated interfaces <https://snapcraft.io/docs/supported-interfaces>`__ to access the host machine. \* **CI/CD integration**: The creation of snaps can be integrated into your CI pipeline, making the updates effortless. \* **OTA and delta updates**: Snaps can update `automatically and transactionally <https://snapcraft.io/docs/keeping-snaps-up-to-date>`__, making sure the device is never broken. \* **Multi-architecture**: Snaps come with a `multi-architecture feature <https://snapcraft.io/docs/architectures>`__, allowing you to build your snap package for multiple architectures. \* **Managing updates**: Snaps can be `updated automatically or you can control the update <https://snapcraft.io/docs/keeping-snaps-up-to-date>`__ options (update hours, update holds, update history). It also comes with `multiple release channels <https://snapcraft.io/docs/channels>`__ for role-based access controls and application versioning. \* **Reduce boot time**: You can configure a snap application as a daemon, so it starts automatically at boot.

ROS deployment solution
-----------------------

`Snapcraft <https://snapcraft.io/docs/snapcraft-overview>`__ comes with native integrations through plugins and extensions dedicated to both `ROS <https://snapcraft.io/docs/ros-applications>`__ and `ROS 2 <https://snapcraft.io/docs/ros2-applications>`__; developed and maintained by Canonical.

Follow the step-by-step instructions below to create your first ROS snap.

Get started now
---------------

**ROS 1** \| \| \| \|–|–\| \| :ref:`ROS applications <7822>` \| Learn how to create a ROS snap for your application\| \| :ref:`catkin <8644>` \| Use the Catkin plugin to generate your ROS1 package\| \| :ref:`catkin-tools <8645>` \| Use the Catkin plugin to compile your ROS package \| \| :ref:`ROS extension <20070>` \| ROS extension helps you snap ROS applications. It comes along with caktin or catkin-tools plugins, adds the ROS APT package repository and sets a build and run-time environment.

**ROS 2** \| \| \| \|–|–\| \| :ref:`ROS 2 applications <7823>` \| Learn how to create a ROS 2 snap for your application \| \| :ref:`colcon <11895>` \| Use the Colcon plugin to build your ROS 2 package \| \| :ref:`ROS 2 Foxy extension <19639>` \| ROS 2 Foxy extension helps you snap ROS 2 applications. It comes along with the colcon plugin, adds the ROS 2 APT package repository and sets a build and run-time environment. \| \| :ref:`ROS 2 Humble extension <30809>` \| ROS 2 Humble extension helps you snap ROS 2 applications. It comes along with the colcon plugin, adds the ROS 2 APT package repository and sets a build and run-time environment. \| \| :ref:`ROS 2 shared memory <31214>` \| Learn about ROS 2 shared-memory in snaps

**Others** \| \| \| \|–|–\| \| :ref:`ROS architectures with snaps <35431>` \| Presentation of the different snap architectures that developers can adopt for their ROS applications \| \| `ROS FAQ & troubleshooting <https://forum.snapcraft.io/t/29208>`__ \| FAQ & troubleshooting about snap and ROS integration \| \| :ref:`ROS snap with GitHub Actions <30605>` \| Build and Publish a ROS Snap with GitHub Actions \|

.. toctree::
   :hidden:

   ros-deployment-with-snaps
   ros-2-deployment-with-snaps
   docker-to-snap
   build-and-publish-a-ros-snap-with-github-actions
   ros-2-shared-memory-in-snaps
   ros-distributions-with-no-extensions
   cross-compile-an-autotools-project