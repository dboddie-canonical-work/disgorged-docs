.. 12231.md

.. \_parts-lifecycle:

Parts lifecycle
===============

Parts, alongside `plugins <snapcraft-plugins.md>`__, are a key component in any `Snapcraft <snapcraft-overview.md>`__ project.

See `Adding parts <adding-parts.md>`__ for a general overview of what parts are and how to use them and `Scriptlets <override-build-steps.md>`__ for details on how they can be scripted outside of *snapcraft.yaml*.

All parts within a project, by means of the logic encoded the plugins they’re using, all go through the same series of steps. Knowing these steps, and which directories are used for each step, can help when creating more advanced snaps, and when troubleshooting build issues.

-  `Lifecycle steps <#parts-lifecycle-heading--steps>`__
-  `Step dependencies <#parts-lifecycle-heading--step-dependencies>`__
-  `Parts directories <#parts-lifecycle-heading--parts-directories>`__

--------------

.. raw:: html

   <h3 id="parts-lifecycle-heading--steps">

Lifecycle steps⚓

.. raw:: html

   </h3>

The steps a part goes through are as follows:

1. **pull**: downloads or otherwise retrieves the components needed to build the part. You can use the ```source-*`` keywords <snapcraft-parts-metadata.md#parts-lifecycle-heading--source>`__ of a part to specify which components to retrieve. If ``source`` points to a git repository, for example, the pull step will clone that repository.
2. **build**: constructs the part from the previously pulled components. The ```plugin`` <snapcraft-plugins.md>`__ of a part specifies how it is constructed. The ```meson`` plugin <the-meson-plugin.md>`__, for example, executes ``meson`` and ``ninja`` to compile source code. Each part is built in a separate directory, but it can use the contents of the staging area if it specifies a dependency on other parts using the ``after`` keyword. See `Step dependencies <#parts-lifecycle-heading--step-dependencies>`__ for more information.
3. **stage**: copies the built components into the staging area. This is the first time all the different parts that make up the snap are actually placed in the same directory. If multiple parts provide the same file with differing contents, you will get a conflict. You can avoid these conflicts by using the ```stage`` keyword <snapcraft-parts-metadata.md#parts-lifecycle-heading--stage>`__ to enable or block files coming from the part. You can also use this keyword to filter out files that are not required in the snap itself, for example build files specific to a single part.
4. **prime**: copies the staged components into the priming area, to their final locations for the resulting snap. This is very similar to the stage step, but files go into the priming area instead of the staging area. The ``prime`` step exists because the staging area might still contain files that are required for the build but not for the snap. For example, if you have a part that downloads and installs a compiler, then you stage this part so other parts can use the compiler during building. You can then use the ``prime`` filter keyword to make sure that it doesn’t get copied to the priming area, so it’s not taking up space in the snap. Some extra checks are also run during this step to ensure that all dependencies are satisfied for a proper run time. If confinement was set to ``classic``, then files will be scanned and, if needed, patched to work with this confinement mode.

Finally, **snap** takes the entire contents of the ``prime`` directory and packs it into `a snap <the-snap-format.md>`__.

Each of these lifecycle steps can be run from the command line, and the command can be part specific or apply to all parts in a project.

1. ``snapcraft pull [<part-name>]``
2. ``snapcraft build [<part-name>]``
3. ``snapcraft stage [<part-name>]``
4. ``snapcraft prime [<part-name>]``
5. ``snapcraft snap`` or ``snapcraft``

Note that each command also executes the previous lifecycle steps, so ``snapcraft`` executes all the lifecycle steps chained together.

To access the part environment at any stage, add the ``--shell`` argument. For example, ``snapcraft prime --shell`` will run up to the *prime* step and open a shell. See `Iterating over a build <iterating-over-a-build.md>`__ for more details.

.. raw:: html

   <h3 id="parts-lifecycle-heading--step-dependencies">

Step dependencies⚓

.. raw:: html

   </h3>

Each lifecycle step depends on the completion of the previous step for that part, so to reach a desired step, all prior steps need to have successfully run. By default, ``snapcraft`` runs the same lifecycle step of all parts before moving to the next step. However, you can change this behavior using the ``after`` keyword in the definition of a part in ``snapcraft.yaml``. This creates a dependency chain from one part to another.

.. code:: yaml

    grv:
       plugin: go
       go-channel: 1.11/stable
       after:
         - libgit2

In the above example, the part named ``grv`` will be built after the part named ``libgit2`` has been successfully built *and* staged.

.. raw:: html

   <h3 id="parts-lifecycle-heading--overriding-steps">

Overriding a step⚓

.. raw:: html

   </h3>

Each plugin defines the default actions that happen during a step. This behavior can be changed in two ways.

-  By using ``override-<step-name>`` in ``snapcraft.yaml``. See `Overriding steps <override-build-steps.md>`__ for more details.
-  By using a local plugin. This can inherit the parent plugin or scaffolding from the original. See `Local plugins <writing-local-plugins.md>`__ for more details.

See `Parts environment variables <parts-environment-variables.md>`__ for a list of part-specific environment variables that can be accessed to help build a part.

.. raw:: html

   <h3 id="parts-lifecycle-heading--parts-directories">

Parts directories⚓

.. raw:: html

   </h3>

When running through its build steps, a part will use different working directories. These closely follow the step names for the lifecycle.

+----------------------------+-----------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Environment variable       | Directory                                     | Purpose                                                                                                                                                                   |
+============================+===============================================+===========================================================================================================================================================================+
| ``SNAPCRAFT_PART_SRC``     | **``parts/<part-name>/src``**                 | the location of the source during the *pull* step                                                                                                                         |
+----------------------------+-----------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``SNAPCRAFT_PART_BUILD``   | **``parts/<part-name>/build``**               | the working directory during the *build* step                                                                                                                             |
+----------------------------+-----------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``SNAPCRAFT_PART_INSTALL`` | **``parts/<part-name>/install``**             | contains the results of the *build* step and the stage packages.                                                                                                          |
+----------------------------+-----------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``SNAPCRAFT_STAGE``        | **``stage``**                                 | shared by all parts, this directory contains the development libraries, headers, and other components (e.g.; pkgconfig files) that need to be accessible from other parts |
+----------------------------+-----------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``SNAPCRAFT_PRIME``        | **``prime``**                                 | shared by all parts, this directory holds the final components for the resulting snap.                                                                                    |
+----------------------------+-----------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

The following table gives an overview of which directories each step uses. The directories are specified by their environment variables.

.. raw:: html

   <!--
   | Step | Explanation | Source&nbsp;directory&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| Result directory |
   |--|--|--|--|
   | **pull** | downloads and retrieves the sources | *as specified by [`source`](snapcraft-parts-metadata.md#parts-lifecycle-heading--source) key* | SNAPCRAFT_PART_**SRC** |
   | **build** <br> *organise*  | builds the part <br> renames built files | SNAPCRAFT_PART_**BUILD** <br> SNAPCRAFT_PART_**INSTALL** | SNAPCRAFT_PART_**INSTALL** <br> SNAPCRAFT_PART_**INSTALL** |
   | **stage** | copies built files to shared stage directory | SNAPCRAFT_PART_**INSTALL** | SNAPCRAFT_**STAGE** |
   | **prime** | copies staged files to shared prime directory | SNAPCRAFT_PART_**INSTALL*** | SNAPCRAFT_**PRIME** |
   | **snap** | packs contents of prime directory into a snap | SNAPCRAFT_**PRIME** | SNAPCRAFT_PROJECT_DIR |
   -->

+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Step                              | Explanation                                                                                                                                                                      |
+===================================+==================================================================================================================================================================================+
| **pull**                          | downloads and retrieves the sources specified by the ```source`` <snapcraft-parts-metadata.md#parts-lifecycle-heading--source>`__ key and puts them in SNAPCRAFT_PART\_\ **SRC** |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **build**                         | builds the sources in SNAPCRAFT_PART\_\ **BUILD** and places the result in SNAPCRAFT_PART\_\ **INSTALL**                                                                         |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **organize**                      | renames built files in SNAPCRAFT_PART\_\ **INSTALL**                                                                                                                             |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **stage**                         | copies built files from SNAPCRAFT_PART\_\ **INSTALL** to the shared SNAPCRAFT\_\ **STAGE**                                                                                       |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **prime**                         | copies the *staged* files from the shared SNAPCRAFT\_\ **STAGE** to the shared SNAPCRAFT\_\ **PRIME**                                                                            |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| **snap**                          | packs contents of SNAPCRAFT\_\ **PRIME** into a snap and puts the snap in SNAPCRAFT_PROJECT_DIR                                                                                  |
+-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+