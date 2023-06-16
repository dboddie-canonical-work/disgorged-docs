.. 29407.md

.. _release-notes-snapcraft-6-1:

# Release notes: Snapcraft 6.1

The team behind Snapcraft is pleased to announce the release of [Snapcraft 6.1](https://github.com/snapcore/snapcraft/releases/tag/6.1).

Among its many updates, fixes and additions, the following are what we consider its highlights:

- Git sources can now configure how sub-modules are fetched
- Plugin updates to NPM, Autotools, Gradle and ROS2
- LZO compression by default for the KDE extension

For general details, including installation instructions, see [Snapcraft overview](https://snapcraft.io/docs/snapcraft-overview), or take a look at [Snapcraft release notes](https://snapcraft.io/docs/snapcraft-release-notes) for other *Snapcraft* releases.

- [Git sources](#heading--git)
- [Plugins](#heading--plugins)
- [Extensions](#heading--extensions)
- [Command line interface](#heading--cli)
- [core22 parts lifecycle opt-in for core20](#heading--core22)
- [Schema](#heading--schema)
- [Other fixes](#heading-other)
- [New contributors](#heading--contribs)
---

<h2 id='heading--git'>Git Sources</h2>

-   sources: make submodule fetching configurable by [@mr-cal](https://github.com/mr-cal) in [#3629](https://github.com/snapcore/snapcraft/pull/3629)

More fine grained source fetching, three new scenarios are supported:

1.  fetching only listed submodules, in the defined `source-submodules`

```source-yaml
parts:
  git-test:
    plugin: dump
    source-type: git
    source: git@github.com...
    source-submodules:
      - submodule_1
      - dir1/submodule_2
```

1.  excluding all submodules with an empty list

```source-yaml
parts:
  git-test:
    plugin: dump
    source-type: git
    source: git@github.com...
    source-submodules: []
```

1.  not defined (the default), all submodules are fetched

<h2 id='heading--plugins'>Plugins</h2>

### NPM plugin

-   npm plugin: allow running as root by [@om26er](https://github.com/om26er) in [#3624](https://github.com/snapcore/snapcraft/pull/3624)
-   npm plugin: extract node archive without preserving ownership by [@om26er](https://github.com/om26er) in [#3625](https://github.com/snapcore/snapcraft/pull/3625)

### Autotools

-   Autotools Plugin (v1): Fix fatal crash when running autogen.sh or bootstrap by [@diddledani](https://github.com/diddledani) in [#3628](https://github.com/snapcore/snapcraft/pull/3628)

### Gradle

-   feat: add support for JDK 17 in the Gradle plugin by [@lupino3](https://github.com/lupino3) in [#3661](https://github.com/snapcore/snapcraft/pull/3661)

### ROS

-   ROS plugins v2: respect source-subdir key by [@Guillaumebeuzeboc](https://github.com/Guillaumebeuzeboc) in [#3664](https://github.com/snapcore/snapcraft/pull/3664)
-   colcon v2: forward cmake args by [@artivis](https://github.com/artivis) in [#3638](https://github.com/snapcore/snapcraft/pull/3638)

<h2 id='heading--extensions'>Extensions</h2>

### KDE

-   extension: compose and dead-keys for neon by [@sergiusens](https://github.com/sergiusens) in [#3643](https://github.com/snapcore/snapcraft/pull/3643)
-   set lzo compression by default in kde-neon extension by [@jriddell](https://github.com/jriddell) in [#3595](https://github.com/snapcore/snapcraft/pull/3595)
-   kde extension: new content snap for core20 by [@jriddell](https://github.com/jriddell) in [#3658](https://github.com/snapcore/snapcraft/pull/3658)

<h2 id='heading--cli'>Command Line Interface</h2>

-   dependencies: missing library resolution by [@mr-cal](https://github.com/mr-cal) in [#3634](https://github.com/snapcore/snapcraft/pull/3634)
-   cli: reintroduce remote-build and promote to snapcraft help by [@aritra24](https://github.com/aritra24) in [#3648](https://github.com/snapcore/snapcraft/pull/3648)

Since the `/usr` merge with `/` the potentially missing stage-packages to add and solve missing dependencies was not working correctly on core20, this has now been fixed

The two command line client commands that were previously hidden, `promote` and `remote-build`, are now displayed as part of the general help.

<h2 id='heading--core22'>core22 parts lifecycle opt-in for core20</h2>

-   lifecycle: core22 lifecycle conditional on build-attributes entry by [@sergiusens](https://github.com/sergiusens) in [#3622](https://github.com/snapcore/snapcraft/pull/3622)
-   lifecycle: fix behavior for core22-step-dependencies by [@facundobatista](https://github.com/facundobatista) in [#3641](https://github.com/snapcore/snapcraft/pull/3641)

To make use of this feature, something like this is needed

```source-yaml
parts:
    part1:
        source: ....
        plugin: make
        build-attributes: [core22-step-dependencies]
```

<h2 id='heading--schema'>Schema</h2>

-   schema: add support for activates-on app property to schema by [@jhenstridge](https://github.com/jhenstridge) in [#3425](https://github.com/snapcore/snapcraft/pull/3425)

<h2 id='heading--other'>Other fixes</h2>

-   spread: update error when local snap is missing by [@sergiusens](https://github.com/sergiusens) in [#3640](https://github.com/snapcore/snapcraft/pull/3640)
-   tools: update staging store URL for uploading blobs by [@nessita](https://github.com/nessita) in [#3656](https://github.com/snapcore/snapcraft/pull/3656)
-   tests: update spread url by [@mr-cal](https://github.com/mr-cal) in [#3663](https://github.com/snapcore/snapcraft/pull/3663)
-   docker: fix Python installation by [@mhoeher](https://github.com/mhoeher) in [#3607](https://github.com/snapcore/snapcraft/pull/3607)
-   build(deps): bump pyyaml from 5.3 to 5.4 by [@dependabot](https://github.com/dependabot) in [#3490](https://github.com/snapcore/snapcraft/pull/3490)

<h2 id='heading--contribs'>New Contributors</h2>


-   [@om26er](https://github.com/om26er) made their first contribution in [#3624](https://github.com/snapcore/snapcraft/pull/3624)
-   [@aritra24](https://github.com/aritra24) made their first contribution in [#3648](https://github.com/snapcore/snapcraft/pull/3648)
-   [@lupino3](https://github.com/lupino3) made their first contribution in [#3661](https://github.com/snapcore/snapcraft/pull/3661)
-   [@mhoeher](https://github.com/mhoeher) made their first contribution in [#3607](https://github.com/snapcore/snapcraft/pull/3607)
-   [@Guillaumebeuzeboc](https://github.com/Guillaumebeuzeboc) made their first contribution in [#3664](https://github.com/snapcore/snapcraft/pull/3664)