.. 8584.md

.. _the-dotnet-plugin:

# The dotnet plugin

The `dotnet` plugin is used to build [.NET Core](https://github.com/dotnet/core) runtime parts.

The plugin uses the .NET SDK to install dependencies via the [NuGet](https://www.nuget.org/) package manager, and follows the standard semantics for a .NET Core  project.

Plugin-specific features and syntax are dependent on which [base](/t/base-snaps/11198) is being used, as outlined below:

- [base: core22](#heading--core22)
- [base: core18 | core](#heading--core18)

For examples, search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+dotnet%22&type=Code) for projects using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.

<h3 id='heading--core22'>base: core22</h3>

This plugin uses the following plugin-specific keywords:

 - **`dotnet-build-configuration`** (string, default: _Release_)
      The dotnet build configuration to use.

 - **`dotnet-self-contained-runtime-identifier`** (string)
      Runtime identifier to use when building a self-contained application (e.g. _linux-x64_).

Requires Snapcraft version _7.0+_.

<h3 id='heading--core18'>base: core18 | core</h3>

This plugin uses the following plugin-specific keywords:

- **`debug`**: builds using a Debug configuration.

Requires Snapcraft version _3.x+_.