.. 8584.md

.. \_the-dotnet-plugin:

The dotnet plugin
=================

The ``dotnet`` plugin is used to build `.NET Core <https://github.com/dotnet/core>`__ runtime parts.

The plugin uses the .NET SDK to install dependencies via the `NuGet <https://www.nuget.org/>`__ package manager, and follows the standard semantics for a .NET Core project.

Plugin-specific features and syntax are dependent on which `base <base-snaps.md>`__ is being used, as outlined below:

-  `base: core22 <#the-dotnet-plugin-heading--core22>`__
-  `base: core18 \| core <#the-dotnet-plugin-heading--core18>`__

For examples, search `GitHub <https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+dotnet%22&type=Code>`__ for projects using the plugin.

   ⓘ This is a *snapcraft* plugin. See `Snapcraft plugins <snapcraft-plugins.md>`__ and `Supported plugins <supported-plugins.md>`__ for further details on how plugins are used.

.. raw:: html

   <h3 id="the-dotnet-plugin-heading--core22">

base: core22

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keywords:

-  **``dotnet-build-configuration``** (string, default: *Release*) The dotnet build configuration to use.

-  **``dotnet-self-contained-runtime-identifier``** (string) Runtime identifier to use when building a self-contained application (e.g. *linux-x64*).

Requires Snapcraft version *7.0+*.

.. raw:: html

   <h3 id="the-dotnet-plugin-heading--core18">

base: core18 \| core

.. raw:: html

   </h3>

This plugin uses the following plugin-specific keywords:

-  **``debug``**: builds using a Debug configuration.

Requires Snapcraft version *3.x+*.
