.. 8633.md

.. \_the-kbuild-plugin:

The kbuild plugin
=================

The ``kbuild`` plugin can be used when working with `kBuild <http://trac.netlabs.org/kbuild/wiki/kBuild>`__-based projects, commonly used to build the Linux kernel.

   ⓘ This plugin is only available to *core* and *core18* based snaps. See `Base snaps <base-snaps.md>`__ for details.

The plugin applies your selected *defconfig* first by running ``make defconfig``. The *kconfigs* flag is then used to augment the resulting config by prepending the configured *kconfigs* values to the ``.config`` and then running ``"yes" "" | make oldconfig``. The result is an updated ``.config`` file.

If *kconfigfile* is provided by the user, it’s used as the starting point for this plugin instead of executing ``make $kdefconfig``.

If both *kdefconfig* and **kconfigfile** are provided, the above *kconfigfile* process will be used.

This plugin is built on `snapcraft.BasePlugin <snapcraft-plugin-api.md>`__ and inherits the same properties, with the following additional kBuild-specific options:

-  **``kdefconfig``** (list of kdefconfigs) Defconfig target to use as the base configuration. Default: “defconfig”

-  **``kconfigfile``** (filepath) Path to file to use as base configuration. If provided this option wins over everything else. Default: None

-  **``kconfigflavour``** (string) Ubuntu config flavour to use as base configuration. If provided this option wins over *kdefconfig*. Default: None

-  **``kconfig``** (list of strings) Explicit list of configs to force; this will override the configs that were set as base through *kdefconfig* and *kconfigfile* and dependent configs will be fixed using the defaults encoded in the *kbuild* config definitions. If you don’t want default for one or more implicit configs coming out of these, just add them to this list as well.

See `The kernel plugin <the-kernel-plugin.md>`__ for additional options related to building a kernel snap.

For examples, search `GitHub <https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+kbuild%22&type=Code>`__ for projects already using the plugin.

   ⓘ This is a *snapcraft* plugin. See `Snapcraft plugins <snapcraft-plugins.md>`__ and `Supported plugins <supported-plugins.md>`__ for further details on how plugins are used.
