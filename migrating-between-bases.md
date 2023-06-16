.. 23455.md

.. _migrating-between-bases:

# Migrating between bases

A *base* snap is a special kind of snap that provides a run-time environment with a minimal set of libraries that are common to most applications. They're transparent to users, but they need to be considered and specified when building a snap.

See [Base snaps](/t/base-snaps/11198) for details on how use and specify them.

Each base snap is built from a [corresponding Ubuntu LTS ](/t/base-snaps/11198#heading--supported) release and migrating a snap from one base to the next gives the snap access to newer packages, extended support, and the latest [Snapcraft](/t/snapcraft-overview/8940) features, including [plugins](/t/supported-plugins/8080) and [extensions](/t/snapcraft-extensions/13486).

The complexity of the migration process is directly linked to both dependencies in the snap's [snapcraft.yaml](/t/the-snapcraft-format/8337) and the base snap versions being migrated between.

At its simplest, migrating from one base snap to another requires only that the  _base_ keyword is updated:

```diff
- base: core18
+ base: core20
```

But further changes will most likely be needed, and what these are will depend on the original base and the packages that are bundled alongside the application. The most common required changes are described below:

- [No base, or old bases](#heading--oldbase)
- [Package names](#heading--names)
- [Architectures](#heading--arch)
- [Environment variables](#heading--environment)
- [Remote parts and extensions](#heading--remote)
- [Audio _interfaces_](#heading--audio)
- [Version scripts](#heading--version)
- Plugins
  - [name changes](#heading--names): nodejs to npm
  - [modified syntax](#heading--syntax): npm, autotools, go,
- [Application definitions](#heading--definitions)
  - [paths](#heading--paths)
  - [command-chain](#heading--command-chain)
- [Migrated snap examples](#heading--examples)
---

<h2 id='heading--oldbase'>Updating from no or old bases</h2>

Migrating a snap from having no base, or `base: core`, to `core18` or `core20`, for example, is a more involved process than going from `core18` to `core20`.

This is because when building a snap with an old base, Snapcraft will operate in compatibility mode.

Compatibility mode is essentially a prior (2.43-era) version of Snapcraft, and will lose the functionality of newer releases. See [Features incompatible with bases](/t/release-notes-snapcraft-3-0/10704#heading--base-exceptions) for details.

<h2 id='heading--names'>Package names</h2>

The `build-packages` and `stage-packages` sections in a snap's [snapcraft.yaml](/t/the-snapcraft-format/8337) specify which packages need to be incorporated during the build and stage parts of the [Parts lifecycle](/t/parts-lifecycle/12231), and described in [Build and staging dependencies](/t/build-and-staging-dependencies/11451).

When no base or _core_ is specified, packages from the Ubuntu 16.04 LTS archive are used at build and stage time. The `core18` base will use packages from the Ubuntu 18.04 LTS archive, whereas the `core20` base will consume packages from the Ubuntu 20.04 LTS archive, and package names can change between releases.

Package name example: [Irssi](https://github.com/snapcrafters/irssi/pull/9)

```diff
    stage-packages:
-      - libperl5.22
+      - libperl5.26
```

In the above example, the name of the Perl library package changed due to a version bump. The best way to resolve these issues is to first build your snap on the destination base system, either via _snapcraft_ or a virtual machine/LXD container, and update each unresolved package in turn with the new equivalents.

<h2 id='heading--arch'>Architectures</h2>

The *architectures* keyword defines a set of both build and run architectures:

```yaml
architectures:
  - build-on: amd64
    run-on: amd64
```

Snaps that produce i386 builds are supportable for the lifetime of Ubuntu 16.04 LTS or Ubuntu 18.04 LTS when using the core or core18 snaps as the base, but `base: core20` does not support the i386 architecture.

Publishers who want to move to ‘base: core20’ must drop builds for the i386 architecture since it isn’t unavailable. Supported `core20` architectures are listed below:

```yaml
architectures:
  - build-on: amd64
  - build-on: arm64
  - build-on: armhf
  - build-on: ppc64el
  - build-on: s390x
```

For potential approaches to maintain an i386 build of a snap, see [How best to handle i386 when moving to core20](https://forum.snapcraft.io/t/how-to-best-handle-i386-when-moving-a-snap-to-base-core20/17680).

<h2 id='heading--environment'>Environment variables</h2>

Environment variables are often used in snaps to ensure binaries are able to find loadable modules or libraries which reside inside the snap at runtime. Sometimes this results in path names which require updates due to directory name changes between versions.

Environment variables example: [Irssi](https://github.com/snapcrafters/irssi/pull/9)

```diff
    environment:
-        PERL5LIB:  "$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl-base/:$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl5/5.22/:$SNAP/usr/share/perl5/:$SNAP/usr/share/perl/5.22.1/:$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl/5.22/:$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl/5.22.1/"
+        PERL5LIB:  "$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl-base/:$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl5/5.26/:$SNAP/usr/share/perl5/:$SNAP/usr/share/perl/5.26.1/:$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl/5.26/:$SNAP/usr/lib/$SNAPCRAFT_ARCH_TRIPLET/perl/5.26.1/"
```

When a package name changes or is updated, it's worth checking to make sure no environment variables are dependent on a path related to an older name, as with the above path.

<h2 id='heading--remote'>Remote parts and Extensions</h2>

In some snaps [remote parts](/t/remote-reusable-parts/4233) may have been used to share configuration across multiple snaps and to reduce the local `snapcraft.yaml` complexity.

These parts are defined elsewhere, and would be incorporated at build time. This functionality is deprecated, so remote parts should be pasted directly into the `snapcraft.yaml` or referenced from their source repository.

Example of pasted remote part: [Mr Rescue](https://github.com/snapcrafters/mrrescue/pull/6)

```diff
 parts:
   mrrescue:
-    after:
-      - desktop-glib-only
+    desktop-glib-only:
+	   build-packages:
+	     - libglib2.0-dev
+	   plugin: make
+	   source: https://github.com/ubuntu/snapcraft-desktop-helpers.git
+	   source-subdir: glib-only
+	   stage-packages:
+	     - libglib2.0-bin
```

Alternatively for some desktop applications it may be appropriate to switch to using an extension, which simplifies the `snapcraft.yaml` further. This is covered in [Snapcraft Extensions](/t/snapcraft-extensions/13486).

Example migration to an Extension: [Xonotic](https://github.com/snapcrafters/xonotic/pull/6)


```diff
 parts:
   xonotic:
-    after:
-      - desktop-glib-only
 apps:
   xonotic:
-    command: desktop-launch $SNAP/Xonotic/xonotic-linux-sdl.sh
+    extensions: [gnome-3-34]
+    command: Xonotic/xonotic-linux-sdl.sh
```

In the above example, we remove the reference to a remote part `desktop-glib-only` and instead use the `extensions` section to use the `gnome-3-34` extension, which replaces the functionality of the remote part.

### Extension naming

Not all extensions work on all bases. For example, on `core18` , use the `gnome-3-34` extension and on `core20` use `gnome-3-38`. See [Supported extensions](/t/supported-extensions/20521) for further details.

Example showing `core20`-only Gnome extension: [Dwarf Fortress](https://github.com/ultraviolet-1986/df/pull/3)

```diff
 parts:
   tarball:
-     after: [desktop-gtk3]
 apps:
   dwarffortress:
-    command: desktop-launch $SNAP/wrapper.sh
+    extensions: [gnome-3-38]
+    command: wrapper.sh
```

<h2 id='heading--audio'>Audio <i>interfaces</i></h2>

For applications which play or record audio, the [interface](/t/interface-management/6154) names have changed.
Previously the [pulseaudio](/t/the-pulseaudio-interface/7906) interface was used for both playback and recording of audio. This has been replaced by [audio-playback](/t/the-audio-playback-interface/13089) and [audio-record](t/the-audio-record-interface/13090):

Example audio interface update: [Xonotic](https://github.com/snapcrafters/xonotic/pull/6)

```diff
 apps:
   xonotic:
     plugs:
-      pulseaudio
+      audio-playback
```

Note that to ensure privacy, `audio-playback` is automatically connected but `audio-record` is *not*.

Application publishers who believe `audio-record` *should* be automatically connected on install (such as for an audio recording application) should start a thread in the [store-requests](https://forum.snapcraft.io/c/store-requests/19) category on the Snapcraft forum asking for it.

<h2 id='heading--version'>Version scripts</h2>

The top level `version-script` option has been [deprecated](/t/deprecation-notice-10/12463) in favour of `adopt-info`. This requires that you specify `adopt-info` with a reference to the part in which the version data (and some other metadata) may be set.

Within the `parts` section, use `snapcraftctl set-version` to define the snapcraft project version number used at build time.

Example replacing _version-script_ with _adopt-info_: [Cointop](https://github.com/miguelmota/cointop/pull/94)

```diff
-version-script: git -C parts/cointop/build rev-parse --short HEAD
+adopt-info: cointop
 parts:
   cointop:
+    override-pull: |
+      snapcraftctl pull
+      snapcraftctl set-version $(git rev-parse --short HEAD)
```

See [Using external metadata](/t/using-external-metadata/4642) for further details.

<h2 id='#heading--name'>Plugin name changes</h2>

The following plugin names have changed across Snapcraft releases:

### nodejs / npm

The `nodejs` plugin is now `npm`.

e.g. [wethr](https://github.com/snapcrafters/wethr/commit/678ac026fb03d42925eb585f376245ee073747ad)

```diff
 parts:
   wethr:
-    plugin: nodejs
+    plugin: npm
```

<h2 id='heading--syntax'>Plugin syntax</h2>

Plugin changes can be queried with the `snapcraft help <plugin name> --base <base name>` command:

```bash
$ snapcraft help npm --base core20
Displaying help for the 'npm' plugin for 'core20'.
[...]
```

You can also list plugins for a specific base with `snapcraft list-plugins --base <base name>`:

```bash
$ snapcraft list-plugins --base core20
Displaying plugins available for 'core20'
autotools  catkin  catkin-tools  cmake  colcon  dump  go  make
meson nil  npm  python  qmake  rust
```

The following plugins have changed their syntax across Snapcraft releases.

### npm

The [npm plugin](/t/the-npm-plugin/17591) uses `npm-node-version` instead of `node-engine` to specify the version of upstream npm to be used at build time.

Example npm plugin syntax change: [wethr](https://github.com/snapcrafters/wethr/commit/678ac026fb03d42925eb585f376245ee073747ad)

```diff
 parts:
   wethr:
-    node-engine: "10.14.1"
+    npm-node-version: "10.14.1"
```

### autotools

The [Autotools plugin](/t/the-autotools-plugin/8616) has migrated options from `configflags` to `autotools-configure-parameters`.

Example Autotools plugin syntax changes: [Inadyn](https://github.com/snapcrafters/inadyn/commit/ba4f114eb07a3295e40798869c9cf7ce476e8037)

```diff
 parts:
   libconfuse:
    plugin: autotools
-    configflags: ['--prefix=/usr', '--disable-examples', '--disable-static']
+    autotools-configure-parameters: ['--prefix=/usr', '--disable-examples', '--disable-static']
```

### go

The [go plugin](t/the-go-plugin/8505) no longer requires the `go-importpath` to be specified. A `go-channel` should be specified.

Example Go plugin syntax changes:  [slack-term](https://github.com/snapcrafters/slack-term/commit/bca6333f64297a1c117b8fc9560eb92b427e0ea7)

```diff
 parts:
   slack-term:
     plugin: go
-      go-importpath: github.com/erroneousboat/slack-term
+      go-channel: latest/stable
```

<h2 id='heading--definitions'>Application definitions</h2>

<h3 id='heading--paths'>Paths</h3>

Snapcraft now requires explicit paths to be specified for binaries listed in the `apps` stanza:

Example update adding explicit paths: [wethr](https://github.com/snapcrafters/wethr/commit/678ac026fb03d42925eb585f376245ee073747ad)

```diff
 apps:
   wethr:
-    command: wethr
+    command: bin/wethr
```

<h3 id='heading--command-chain'>command-chain</h3>

Rather than specify `command` followed by a long list of space-separated executables, they can now be listed with the [command-chain](/t/snapcraft-app-and-service-metadata/8335#heading--command-chain) option:

Example of command being replaced by command-chain: [Atom](https://github.com/snapcrafters/atom/pull/64)

```diff
 apps:
   atom:
-    command: bin/launcher ${SNAP}/usr/share/atom/atom
+    command-chain:
+      - bin/launcher
+    command: usr/share/atom/atom
```

<h2 id='heading--examples'>Examples summary</h2>

* [Atom](https://github.com/snapcrafters/atom/pull/64)
* [Cointop](https://github.com/miguelmota/cointop/pull/94)
* [ddgr](https://github.com/snapcrafters/ddgr/pull/3)
* [Duck Marines](https://github.com/snapcrafters/duckmarines/pull/5)
* [Dwarf Fortress](https://github.com/ultraviolet-1986/df/pull/3)
* [Irssi](https://github.com/snapcrafters/irssi/pull/9)
* [Mr Rescue](https://github.com/snapcrafters/mrrescue/pull/6)
* [slack-term](https://github.com/snapcrafters/slack-term/commit/bca6333f64297a1c117b8fc9560eb92b427e0ea7)
* [wethr](https://github.com/snapcrafters/wethr/commit/678ac026fb03d42925eb585f376245ee073747ad)
* [Xonotic](https://github.com/snapcrafters/xonotic/pull/6)