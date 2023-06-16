.. 23455.md

.. \_migrating-between-bases:

Migrating between bases
=======================

A *base* snap is a special kind of snap that provides a run-time environment with a minimal set of libraries that are common to most applications. They’re transparent to users, but they need to be considered and specified when building a snap.

See `Base snaps <base-snaps.md>`__ for details on how use and specify them.

Each base snap is built from a `corresponding Ubuntu LTS <base-snaps.md#migrating-between-bases-heading--supported>`__ release and migrating a snap from one base to the next gives the snap access to newer packages, extended support, and the latest `Snapcraft <snapcraft-overview.md>`__ features, including `plugins <supported-plugins.md>`__ and `extensions <snapcraft-extensions.md>`__.

The complexity of the migration process is directly linked to both dependencies in the snap’s `snapcraft.yaml <the-snapcraft-yaml-schema.md>`__ and the base snap versions being migrated between.

At its simplest, migrating from one base snap to another requires only that the *base* keyword is updated:

.. code:: diff

   - base: core18
   + base: core20

But further changes will most likely be needed, and what these are will depend on the original base and the packages that are bundled alongside the application. The most common required changes are described below:

-  `No base, or old bases <#migrating-between-bases-heading--oldbase>`__

-  `Package names <#migrating-between-bases-heading--names>`__

-  `Architectures <#migrating-between-bases-heading--arch>`__

-  `Environment variables <#migrating-between-bases-heading--environment>`__

-  `Remote parts and extensions <#migrating-between-bases-heading--remote>`__

-  `Audio interfaces <#migrating-between-bases-heading--audio>`__

-  `Version scripts <#migrating-between-bases-heading--version>`__

-  Plugins

   -  `name changes <#migrating-between-bases-heading--names>`__: nodejs to npm
   -  `modified syntax <#migrating-between-bases-heading--syntax>`__: npm, autotools, go,

-  `Application definitions <#migrating-between-bases-heading--definitions>`__

   -  `paths <#migrating-between-bases-heading--paths>`__
   -  `command-chain <#migrating-between-bases-heading--command-chain>`__

-  .. rubric:: `Migrated snap examples <#migrating-between-bases-heading--examples>`__
      :name: migrated-snap-examples

.. raw:: html

   <h2 id="migrating-between-bases-heading--oldbase">

Updating from no or old bases

.. raw:: html

   </h2>

Migrating a snap from having no base, or ``base: core``, to ``core18`` or ``core20``, for example, is a more involved process than going from ``core18`` to ``core20``.

This is because when building a snap with an old base, Snapcraft will operate in compatibility mode.

Compatibility mode is essentially a prior (2.43-era) version of Snapcraft, and will lose the functionality of newer releases. See `Features incompatible with bases <release-notes-snapcraft-3-0.md#migrating-between-bases-heading--base-exceptions>`__ for details.

.. raw:: html

   <h2 id="migrating-between-bases-heading--names">

Package names

.. raw:: html

   </h2>

The ``build-packages`` and ``stage-packages`` sections in a snap’s `snapcraft.yaml <the-snapcraft-yaml-schema.md>`__ specify which packages need to be incorporated during the build and stage parts of the `Parts lifecycle <parts-lifecycle.md>`__, and described in `Build and staging dependencies <build-and-staging-dependencies.md>`__.

When no base or *core* is specified, packages from the Ubuntu 16.04 LTS archive are used at build and stage time. The ``core18`` base will use packages from the Ubuntu 18.04 LTS archive, whereas the ``core20`` base will consume packages from the Ubuntu 20.04 LTS archive, and package names can change between releases.

Package name example: `Irssi <https://github.com/snapcrafters/irssi/pull/9>`__

.. code:: diff

       stage-packages:
   -      - libperl5.22
   +      - libperl5.26

In the above example, the name of the Perl library package changed due to a version bump. The best way to resolve these issues is to first build your snap on the destination base system, either via *snapcraft* or a virtual machine/LXD container, and update each unresolved package in turn with the new equivalents.

.. raw:: html

   <h2 id="migrating-between-bases-heading--arch">

Architectures

.. raw:: html

   </h2>

The *architectures* keyword defines a set of both build and run architectures:

.. code:: yaml

   architectures:
     - build-on: amd64
       run-on: amd64

Snaps that produce i386 builds are supportable for the lifetime of Ubuntu 16.04 LTS or Ubuntu 18.04 LTS when using the core or core18 snaps as the base, but ``base: core20`` does not support the i386 architecture.

Publishers who want to move to ‘base: core20’ must drop builds for the i386 architecture since it isn’t unavailable. Supported ``core20`` architectures are listed below:

.. code:: yaml

   architectures:
     - build-on: amd64
     - build-on: arm64
     - build-on: armhf
     - build-on: ppc64el
     - build-on: s390x

For potential approaches to maintain an i386 build of a snap, see `How best to handle i386 when moving to core20 <17680.md>`__.

.. raw:: html

   <h2 id="migrating-between-bases-heading--environment">

Environment variables

.. raw:: html

   </h2>

Environment variables are often used in snaps to ensure binaries are able to find loadable modules or libraries which reside inside the snap at runtime. Sometimes this results in path names which require updates due to directory name changes between versions.

Environment variables example: `Irssi <https://github.com/snapcrafters/irssi/pull/9>`__

.. code:: diff

       environment:
   -        PERL5LIB:  "$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl-base/:$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl5/5.22/:$SNAP/usr/share/perl5/:$SNAP/usr/share/perl/5.22.1/:$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl/5.22/:$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl/5.22.1/"
   +        PERL5LIB:  "$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl-base/:$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl5/5.26/:$SNAP/usr/share/perl5/:$SNAP/usr/share/perl/5.26.1/:$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl/5.26/:$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl/5.26.1/"

When a package name changes or is updated, it’s worth checking to make sure no environment variables are dependent on a path related to an older name, as with the above path.

.. raw:: html

   <h2 id="migrating-between-bases-heading--remote">

Remote parts and Extensions

.. raw:: html

   </h2>

In some snaps `remote parts <remote-reusable-parts.md>`__ may have been used to share configuration across multiple snaps and to reduce the local ``snapcraft.yaml`` complexity.

These parts are defined elsewhere, and would be incorporated at build time. This functionality is deprecated, so remote parts should be pasted directly into the ``snapcraft.yaml`` or referenced from their source repository.

Example of pasted remote part: `Mr Rescue <https://github.com/snapcrafters/mrrescue/pull/6>`__

.. code:: diff

    parts:
      mrrescue:
   -    after:
   -      - desktop-glib-only
   +    desktop-glib-only:
   +      build-packages:
   +        - libglib2.0-dev
   +      plugin: make
   +      source: https://github.com/ubuntu/snapcraft-desktop-helpers.git
   +      source-subdir: glib-only
   +      stage-packages:
   +        - libglib2.0-bin

Alternatively for some desktop applications it may be appropriate to switch to using an extension, which simplifies the ``snapcraft.yaml`` further. This is covered in `Snapcraft Extensions <snapcraft-extensions.md>`__.

Example migration to an Extension: `Xonotic <https://github.com/snapcrafters/xonotic/pull/6>`__

.. code:: diff

    parts:
      xonotic:
   -    after:
   -      - desktop-glib-only
    apps:
      xonotic:
   -    command: desktop-launch $SNAP/Xonotic/xonotic-linux-sdl.sh
   +    extensions: [gnome-3-34]
   +    command: Xonotic/xonotic-linux-sdl.sh

In the above example, we remove the reference to a remote part ``desktop-glib-only`` and instead use the ``extensions`` section to use the ``gnome-3-34`` extension, which replaces the functionality of the remote part.

Extension naming
----------------

Not all extensions work on all bases. For example, on ``core18`` , use the ``gnome-3-34`` extension and on ``core20`` use ``gnome-3-38``. See `Supported extensions <supported-extensions.md>`__ for further details.

Example showing ``core20``-only Gnome extension: `Dwarf Fortress <https://github.com/ultraviolet-1986/df/pull/3>`__

.. code:: diff

    parts:
      tarball:
   -     after: [desktop-gtk3]
    apps:
      dwarffortress:
   -    command: desktop-launch $SNAP/wrapper.sh
   +    extensions: [gnome-3-38]
   +    command: wrapper.sh

.. raw:: html

   <h2 id="migrating-between-bases-heading--audio">

Audio interfaces

.. raw:: html

   </h2>

For applications which play or record audio, the `interface <interface-management.md>`__ names have changed. Previously the `pulseaudio <the-pulseaudio-interface.md>`__ interface was used for both playback and recording of audio. This has been replaced by `audio-playback <the-audio-playback-interface.md>`__ and `audio-record <t/the-audio-record-interface/13090>`__:

Example audio interface update: `Xonotic <https://github.com/snapcrafters/xonotic/pull/6>`__

.. code:: diff

    apps:
      xonotic:
        plugs:
   -      pulseaudio
   +      audio-playback

Note that to ensure privacy, ``audio-playback`` is automatically connected but ``audio-record`` is *not*.

Application publishers who believe ``audio-record`` *should* be automatically connected on install (such as for an audio recording application) should start a thread in the `store-requests <https://forum.snapcraft.io/c/store-requests/19>`__ category on the Snapcraft forum asking for it.

.. raw:: html

   <h2 id="migrating-between-bases-heading--version">

Version scripts

.. raw:: html

   </h2>

The top level ``version-script`` option has been `deprecated <deprecation-notice-10.md>`__ in favour of ``adopt-info``. This requires that you specify ``adopt-info`` with a reference to the part in which the version data (and some other metadata) may be set.

Within the ``parts`` section, use ``snapcraftctl set-version`` to define the snapcraft project version number used at build time.

Example replacing *version-script* with *adopt-info*: `Cointop <https://github.com/miguelmota/cointop/pull/94>`__

.. code:: diff

   -version-script: git -C parts/cointop/build rev-parse --short HEAD
   +adopt-info: cointop
    parts:
      cointop:
   +    override-pull: |
   +      snapcraftctl pull
   +      snapcraftctl set-version $(git rev-parse --short HEAD)

See `Using external metadata <using-external-metadata.md>`__ for further details.

.. raw:: html

   <h2 id="#migrating-between-bases-heading--name">

Plugin name changes

.. raw:: html

   </h2>

The following plugin names have changed across Snapcraft releases:

nodejs / npm
------------

The ``nodejs`` plugin is now ``npm``.

e.g. `wethr <https://github.com/snapcrafters/wethr/commit/678ac026fb03d42925eb585f376245ee073747ad>`__

.. code:: diff

    parts:
      wethr:
   -    plugin: nodejs
   +    plugin: npm

.. raw:: html

   <h2 id="migrating-between-bases-heading--syntax">

Plugin syntax

.. raw:: html

   </h2>

Plugin changes can be queried with the ``snapcraft help <plugin name> --base <base name>`` command:

.. code:: bash

   $ snapcraft help npm --base core20
   Displaying help for the 'npm' plugin for 'core20'.
   [...]

You can also list plugins for a specific base with ``snapcraft list-plugins --base <base name>``:

.. code:: bash

   $ snapcraft list-plugins --base core20
   Displaying plugins available for 'core20'
   autotools  catkin  catkin-tools  cmake  colcon  dump  go  make
   meson nil  npm  python  qmake  rust

The following plugins have changed their syntax across Snapcraft releases.

npm
---

The `npm plugin <the-npm-plugin.md>`__ uses ``npm-node-version`` instead of ``node-engine`` to specify the version of upstream npm to be used at build time.

Example npm plugin syntax change: `wethr <https://github.com/snapcrafters/wethr/commit/678ac026fb03d42925eb585f376245ee073747ad>`__

.. code:: diff

    parts:
      wethr:
   -    node-engine: "10.14.1"
   +    npm-node-version: "10.14.1"

autotools
---------

The `Autotools plugin <the-autotools-plugin.md>`__ has migrated options from ``configflags`` to ``autotools-configure-parameters``.

Example Autotools plugin syntax changes: `Inadyn <https://github.com/snapcrafters/inadyn/commit/ba4f114eb07a3295e40798869c9cf7ce476e8037>`__

.. code:: diff

    parts:
      libconfuse:
       plugin: autotools
   -    configflags: ['--prefix=/usr', '--disable-examples', '--disable-static']
   +    autotools-configure-parameters: ['--prefix=/usr', '--disable-examples', '--disable-static']

go
--

The `go plugin <t/the-go-plugin/8505>`__ no longer requires the ``go-importpath`` to be specified. A ``go-channel`` should be specified.

Example Go plugin syntax changes: `slack-term <https://github.com/snapcrafters/slack-term/commit/bca6333f64297a1c117b8fc9560eb92b427e0ea7>`__

.. code:: diff

    parts:
      slack-term:
        plugin: go
   -      go-importpath: github.com/erroneousboat/slack-term
   +      go-channel: latest/stable

.. raw:: html

   <h2 id="migrating-between-bases-heading--definitions">

Application definitions

.. raw:: html

   </h2>

.. raw:: html

   <h3 id="migrating-between-bases-heading--paths">

Paths

.. raw:: html

   </h3>

Snapcraft now requires explicit paths to be specified for binaries listed in the ``apps`` stanza:

Example update adding explicit paths: `wethr <https://github.com/snapcrafters/wethr/commit/678ac026fb03d42925eb585f376245ee073747ad>`__

.. code:: diff

    apps:
      wethr:
   -    command: wethr
   +    command: bin/wethr

.. raw:: html

   <h3 id="migrating-between-bases-heading--command-chain">

command-chain

.. raw:: html

   </h3>

Rather than specify ``command`` followed by a long list of space-separated executables, they can now be listed with the `command-chain <snapcraft-app-and-service-metadata.md#migrating-between-bases-heading--command-chain>`__ option:

Example of command being replaced by command-chain: `Atom <https://github.com/snapcrafters/atom/pull/64>`__

.. code:: diff

    apps:
      atom:
   -    command: bin/launcher ${SNAP}/usr/share/atom/atom
   +    command-chain:
   +      - bin/launcher
   +    command: usr/share/atom/atom

.. raw:: html

   <h2 id="migrating-between-bases-heading--examples">

Examples summary

.. raw:: html

   </h2>

-  `Atom <https://github.com/snapcrafters/atom/pull/64>`__
-  `Cointop <https://github.com/miguelmota/cointop/pull/94>`__
-  `ddgr <https://github.com/snapcrafters/ddgr/pull/3>`__
-  `Duck Marines <https://github.com/snapcrafters/duckmarines/pull/5>`__
-  `Dwarf Fortress <https://github.com/ultraviolet-1986/df/pull/3>`__
-  `Irssi <https://github.com/snapcrafters/irssi/pull/9>`__
-  `Mr Rescue <https://github.com/snapcrafters/mrrescue/pull/6>`__
-  `slack-term <https://github.com/snapcrafters/slack-term/commit/bca6333f64297a1c117b8fc9560eb92b427e0ea7>`__
-  `wethr <https://github.com/snapcrafters/wethr/commit/678ac026fb03d42925eb585f376245ee073747ad>`__
-  `Xonotic <https://github.com/snapcrafters/xonotic/pull/6>`__
