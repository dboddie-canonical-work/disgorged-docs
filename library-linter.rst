.. 32229.md

.. \_library-linter:

Library linter
==============

The *library* linter is a `Snapcraft linter <snapcraft-linters.md>`__ that is used to verify whether any ELF file dependencies, typically libraries, are missing from a snap. It also verifies if any libraries are included in a snap but are not used.

-  `How the library linter helps <#library-linter-heading--help>`__
-  `Linter warnings <#library-linter-heading--warnings>`__

   -  `Example <#library-linter-heading--warnings-example>`__

-  `Addressing linter issues <#library-linter-heading--issues>`__

See `Disabling linters <snapcraft-linters.md#library-linter-heading--disable>`__ for details on how to stop this linter running.

--------------

.. raw:: html

   <h2 id="library-linter-heading--help">

How the linter helps

.. raw:: html

   </h2>

If a snapped application depends on libraries neither provided by the `base <base-snaps.md>`__ system, nor included as a dependency, the snap package may execute in an incorrect or unpredictable way. The library linter issues a warning if a missing dependency is detected.

Snap package size can be reduced by removing extra libraries that are not used by the applications in the snap. The library linter issues a warning if unused libraries are detected.

.. raw:: html

   <h2 id="library-linter-heading--warnings">

Linter warnings

.. raw:: html

   </h2>

The library linter will issue a warning if:

-  ELF dependencies are detected as missing from the snap package.
-  Libraries not used by an ELF file in the snap package are detected.

.. raw:: html

   <h3 id="library-linter-heading--warnings-example">

Example

.. raw:: html

   </h3>

The example below shows two missing libraries (``libcaca`` and ``libslang``) and one unused library (``libpng16``).

.. code:: log

   Running linter: library
   Lint warnings:
   - library: my-app: missing dependency 'libcaca.so.0'.
   - library: my-app: missing dependency 'libslang.so.2'.
   - library: libpng16.so.16: unused library 'usr/lib/x86_64-linux-gnu/libpng16.so.16.37.0'.

.. raw:: html

   <h2 id="library-linter-heading--issues">

Addressing issues

.. raw:: html

   </h2>

To address library linter issues, packages containing any missing libraries need to be added to the list of ``stage-packages``. Unused libraries can be removed from ``stage-packages``. See `Build and staging dependencies <build-and-staging-dependencies.md>`__ for further details.