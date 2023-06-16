.. 32211.md

.. \_snapcraft-linters:

Snapcraft linters
=================

A *linter* is an analysis tool that checks for common errors or compatibility issues, usually automatically, or as part of some other process.

Snapcraft (from version 7.2 onwards) includes its own linter functionality when working with snaps using the ``core22`` `base <base-snaps.md>`__.

Snapcraft linters run automatically when a snap is packed unless otherwise `disabled <#snapcraft-linters-heading--disabled>`__.

-  `Available linters <#snapcraft-linters-heading--linters>`__
-  `Disabling linters <#snapcraft-linters-heading--disable>`__

   -  .. rubric:: `Ignore specific files <#snapcraft-linters-heading--disable-files>`__
         :name: ignore-specific-files

.. raw:: html

   <h2 id="snapcraft-linters-heading--linters">

Available linters

.. raw:: html

   </h2>

Snapcraft currently offers the following linters:

-  ```classic`` <classic-linter.md>`__: verifies binary file parameters for snaps using `classic confinement <snap-confinement.md>`__
-  ```library`` <library-linter.md>`__: verifies that no ELF file dependencies, such as libraries, are missing and that no extra libraries are included in the snap package

.. raw:: html

   <h2 id="snapcraft-linters-heading--disable">

Disabling linters

.. raw:: html

   </h2>

Snapcraft linters run automatically when a snap is packed but specific linters can be disabled by specifying a ``ignore`` entry in the ``lint`` section of ``snapcraft.yaml``:

.. code:: yaml

   lint:
     ignore:
       - classic
       - library

The ``ignore`` entry must include one or more `linter names <#snapcraft-linters-heading--linters>`__ for those linters to be disabled.

.. raw:: html

   <h3 id="snapcraft-linters-heading--disable-files">

Ignore specific files

.. raw:: html

   </h3>

To omit specific files from a linter, add their snap location under the linter name:

.. code:: yaml

   lint:
     ignore:
       - classic
       - library:
         - usr/lib/**/libfoo.so*

In the above example, the ``classic`` linter will be disabled entirely, and the ``library`` linter will not run for the files matching the specified file pattern.
