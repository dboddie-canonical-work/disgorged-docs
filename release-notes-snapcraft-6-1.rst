.. 29407.md

.. \_release-notes-snapcraft-6-1:

Release notes: Snapcraft 6.1
============================

The team behind Snapcraft is pleased to announce the release of `Snapcraft 6.1 <https://github.com/snapcore/snapcraft/releases/tag/6.1>`__.

Among its many updates, fixes and additions, the following are what we consider its highlights:

-  Git sources can now configure how sub-modules are fetched
-  Plugin updates to NPM, Autotools, Gradle and ROS2
-  LZO compression by default for the KDE extension

For general details, including installation instructions, see `Snapcraft overview <https://snapcraft.io/docs/snapcraft-overview>`__, or take a look at `Snapcraft release notes <https://snapcraft.io/docs/snapcraft-release-notes>`__ for other *Snapcraft* releases.

-  `Git sources <#release-notes-snapcraft-6-1-heading--git>`__

-  `Plugins <#release-notes-snapcraft-6-1-heading--plugins>`__

-  `Extensions <#release-notes-snapcraft-6-1-heading--extensions>`__

-  `Command line interface <#release-notes-snapcraft-6-1-heading--cli>`__

-  `core22 parts lifecycle opt-in for core20 <#release-notes-snapcraft-6-1-heading--core22>`__

-  `Schema <#release-notes-snapcraft-6-1-heading--schema>`__

-  `Other fixes <#release-notes-snapcraft-6-1-heading-other>`__

-  .. rubric:: `New contributors <#release-notes-snapcraft-6-1-heading--contribs>`__
      :name: new-contributors

.. raw:: html

   <h2 id="release-notes-snapcraft-6-1-heading--git">

Git Sources

.. raw:: html

   </h2>

-  sources: make submodule fetching configurable by `@mr-cal <https://github.com/mr-cal>`__ in `#3629 <https://github.com/snapcore/snapcraft/pull/3629>`__

More fine grained source fetching, three new scenarios are supported:

1. fetching only listed submodules, in the defined ``source-submodules``

.. code:: source-yaml

   parts:
     git-test:
       plugin: dump
       source-type: git
       source: git@github.com...
       source-submodules:
         - submodule_1
         - dir1/submodule_2

1. excluding all submodules with an empty list

.. code:: source-yaml

   parts:
     git-test:
       plugin: dump
       source-type: git
       source: git@github.com...
       source-submodules: []

1. not defined (the default), all submodules are fetched

.. raw:: html

   <h2 id="release-notes-snapcraft-6-1-heading--plugins">

Plugins

.. raw:: html

   </h2>

NPM plugin
----------

-  npm plugin: allow running as root by `@om26er <https://github.com/om26er>`__ in `#3624 <https://github.com/snapcore/snapcraft/pull/3624>`__
-  npm plugin: extract node archive without preserving ownership by `@om26er <https://github.com/om26er>`__ in `#3625 <https://github.com/snapcore/snapcraft/pull/3625>`__

Autotools
---------

-  Autotools Plugin (v1): Fix fatal crash when running autogen.sh or bootstrap by `@diddledani <https://github.com/diddledani>`__ in `#3628 <https://github.com/snapcore/snapcraft/pull/3628>`__

Gradle
------

-  feat: add support for JDK 17 in the Gradle plugin by `@lupino3 <https://github.com/lupino3>`__ in `#3661 <https://github.com/snapcore/snapcraft/pull/3661>`__

ROS
---

-  ROS plugins v2: respect source-subdir key by `@Guillaumebeuzeboc <https://github.com/Guillaumebeuzeboc>`__ in `#3664 <https://github.com/snapcore/snapcraft/pull/3664>`__
-  colcon v2: forward cmake args by `@artivis <https://github.com/artivis>`__ in `#3638 <https://github.com/snapcore/snapcraft/pull/3638>`__

.. raw:: html

   <h2 id="release-notes-snapcraft-6-1-heading--extensions">

Extensions

.. raw:: html

   </h2>

KDE
---

-  extension: compose and dead-keys for neon by `@sergiusens <https://github.com/sergiusens>`__ in `#3643 <https://github.com/snapcore/snapcraft/pull/3643>`__
-  set lzo compression by default in kde-neon extension by `@jriddell <https://github.com/jriddell>`__ in `#3595 <https://github.com/snapcore/snapcraft/pull/3595>`__
-  kde extension: new content snap for core20 by `@jriddell <https://github.com/jriddell>`__ in `#3658 <https://github.com/snapcore/snapcraft/pull/3658>`__

.. raw:: html

   <h2 id="release-notes-snapcraft-6-1-heading--cli">

Command Line Interface

.. raw:: html

   </h2>

-  dependencies: missing library resolution by `@mr-cal <https://github.com/mr-cal>`__ in `#3634 <https://github.com/snapcore/snapcraft/pull/3634>`__
-  cli: reintroduce remote-build and promote to snapcraft help by `@aritra24 <https://github.com/aritra24>`__ in `#3648 <https://github.com/snapcore/snapcraft/pull/3648>`__

Since the ``/usr`` merge with ``/`` the potentially missing stage-packages to add and solve missing dependencies was not working correctly on core20, this has now been fixed

The two command line client commands that were previously hidden, ``promote`` and ``remote-build``, are now displayed as part of the general help.

.. raw:: html

   <h2 id="release-notes-snapcraft-6-1-heading--core22">

core22 parts lifecycle opt-in for core20

.. raw:: html

   </h2>

-  lifecycle: core22 lifecycle conditional on build-attributes entry by `@sergiusens <https://github.com/sergiusens>`__ in `#3622 <https://github.com/snapcore/snapcraft/pull/3622>`__
-  lifecycle: fix behavior for core22-step-dependencies by `@facundobatista <https://github.com/facundobatista>`__ in `#3641 <https://github.com/snapcore/snapcraft/pull/3641>`__

To make use of this feature, something like this is needed

.. code:: source-yaml

   parts:
       part1:
           source: ....
           plugin: make
           build-attributes: [core22-step-dependencies]

.. raw:: html

   <h2 id="release-notes-snapcraft-6-1-heading--schema">

Schema

.. raw:: html

   </h2>

-  schema: add support for activates-on app property to schema by `@jhenstridge <https://github.com/jhenstridge>`__ in `#3425 <https://github.com/snapcore/snapcraft/pull/3425>`__

.. raw:: html

   <h2 id="release-notes-snapcraft-6-1-heading--other">

Other fixes

.. raw:: html

   </h2>

-  spread: update error when local snap is missing by `@sergiusens <https://github.com/sergiusens>`__ in `#3640 <https://github.com/snapcore/snapcraft/pull/3640>`__
-  tools: update staging store URL for uploading blobs by `@nessita <https://github.com/nessita>`__ in `#3656 <https://github.com/snapcore/snapcraft/pull/3656>`__
-  tests: update spread url by `@mr-cal <https://github.com/mr-cal>`__ in `#3663 <https://github.com/snapcore/snapcraft/pull/3663>`__
-  docker: fix Python installation by `@mhoeher <https://github.com/mhoeher>`__ in `#3607 <https://github.com/snapcore/snapcraft/pull/3607>`__
-  build(deps): bump pyyaml from 5.3 to 5.4 by `@dependabot <https://github.com/dependabot>`__ in `#3490 <https://github.com/snapcore/snapcraft/pull/3490>`__

.. raw:: html

   <h2 id="release-notes-snapcraft-6-1-heading--contribs">

New Contributors

.. raw:: html

   </h2>

-  `@om26er <https://github.com/om26er>`__ made their first contribution in `#3624 <https://github.com/snapcore/snapcraft/pull/3624>`__
-  `@aritra24 <https://github.com/aritra24>`__ made their first contribution in `#3648 <https://github.com/snapcore/snapcraft/pull/3648>`__
-  `@lupino3 <https://github.com/lupino3>`__ made their first contribution in `#3661 <https://github.com/snapcore/snapcraft/pull/3661>`__
-  `@mhoeher <https://github.com/mhoeher>`__ made their first contribution in `#3607 <https://github.com/snapcore/snapcraft/pull/3607>`__
-  `@Guillaumebeuzeboc <https://github.com/Guillaumebeuzeboc>`__ made their first contribution in `#3664 <https://github.com/snapcore/snapcraft/pull/3664>`__
