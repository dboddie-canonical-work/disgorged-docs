.. 8588.md

.. _the-rust-plugin:

# The rust plugin

The `rust` plugin is useful for building [Rust](https://www.rust-lang.org/)-based parts using the [Cargo](https://crates.io/) package manager to drive the build.  This plugin uses the common plugin keywords as well as those for [sources](snapcraft-parts-metadata.md#the-rust-plugin-heading--source). For more information, see [Snapcraft parts metadata](snapcraft-parts-metadata.md).

Additional features and syntax are dependent on which [base](base-snaps.md) is being used, as outlined below:

- [base: core22](#the-rust-plugin-heading--core22)
- [base: core20](#the-rust-plugin-heading--core20)
- [base: core18 | core](#the-rust-plugin-heading--core18)

See [Rust applications](rust-applications.md) for a simple example, or search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+rust%22&type=Code) for projects using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](snapcraft-plugins.md) and [Supported plugins](supported-plugins.md) for further details on how plugins are used.

<h3 id='the-rust-plugin-heading--core22'>base: core22</h3>

- **`rust-features`** (list of strings)
     Features used to build optional dependencies
- **`rust-path`** (list of strings)
     Defaults to the current working directory. Can be set to the relative path for the crate to build when using workspaces. Only one item is currently supported.


Requires Snapcraft version _7.0+_.

<h3 id='the-rust-plugin-heading--core20'>base: core20</h3>

- **`rust-features`** (list of strings)
     Features used to build optional dependencies
- **`rust-path`** (list of strings)
     Defaults to the current working directory. Can be set to the relative path for the crate to build when using workspaces. Only one item is currently supported.

Requires Snapcraft version _4.0+_.

<h3 id='the-rust-plugin-heading--core18'>base: core18 | core</h3>

- **`rust-channel`** (string)
     Used to select which *rust* channel (stable, beta, nightly)
- **`rust-features`** (list of strings)
     Features used to build optional dependencies
- **`rust-revision`** (string)
     Used to select which *rust* version

If a  [rust-toolchain](https://rust-lang.github.io/rustup/overrides.html#the-toolchain-file) file is detected, the toolchain it specifies will be used  by default. However, if `rust-channel` or `rust-revision` are set, the rust-toolchain file will be overridden.

If neither a rust-toolchain exists nor `rust-channel` or `rust-revision` are set, the latest stable toolchain will be used.

Requires Snapcraft version _3.x+_.