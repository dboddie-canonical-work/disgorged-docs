.. 24083.md

.. _release-notes-snapcraft-4-6:

# Release notes: Snapcraft 4.6

Snapcraft 4.6 is a feature-packed release, including:
- new extensions
-  _core20_ support for additional extensions and plugins
- a new login mechanism.
- plenty of bug fixes and smaller updates

For general details, including installation instructions, see [Snapcraft overview](https://snapcraft.io/docs/snapcraft-overview), or take a look at [Snapcraft release notes](https://snapcraft.io/docs/snapcraft-release-notes) for other *Snapcraft* releases.

## Login mechanism

A new option, `--experimental-login` can now be used when using `snapcraft login` or `snapcraft export-login` and when signing assertions (see [Create a developer account](create-a-developer-account.md)).

Using this option will trigger a web based authentication flow. To go back to the previous login method you must first `snapcraft logout`.

## Conda plugin

The [conda](the-conda-plugin.md) plugin has been ported to [core20](base-snaps.md). These are the available plugin options:

* **`conda-packages`** (list of strings)
List of *conda* packages to install.
* **`conda-python-version`** (string)
The Python version to use for the *conda* packages.
 Python version major and minor version (e.g. 3.8).
* **`conda-miniconda-version`** (string)
The version of [Miniconda](https://docs.conda.io/en/latest/miniconda.html) to bootstrap.
Defaults to the latest release.


## Package Repositories

The road to making this feature stable is closer, although a breaking change lands with 4.6 for this experimental feature. Keys are now using the suffix and not prefix of the key id.

See [Package repositories](snapcraft-package-repositories.md) for further details.

## Metadata

Snapcraft is now aware of the existence of `kernel.yaml` for snaps of type `kernel`.

The `install-mode` option for applications is now supported with this release.

## Extensions


### Gnome 3.38

The [gnome-3-38 extension](the-gnome-3-38-extension.md) is now considered stable.

### KDE Neon


The [KDE Neon extension](the-kde-neon-extension.md) now supports `core20` as an experimental extension.

### Flutter


New variants of the [Flutter extension](the-flutter-extension.md) are now available for _stable_ and _beta_. The same documentation applies as for the master and dev variant.

Full list of changes
--------------------

-   package-repositories: use last 8 characters of key id for .asc [@cjp256](https://github.com/cjp256) ([#3486](https://github.com/snapcore/snapcraft/pull/3486))
-   build(deps): bump lxml from 4.6.2 to 4.6.3 [@dependabot](https://github.com/dependabot) ([#3485](https://github.com/snapcore/snapcraft/pull/3485))
-   Support install-mode option for apps [@cmatsuoka](https://github.com/cmatsuoka) ([#3482](https://github.com/snapcore/snapcraft/pull/3482))
-   requirements: use PyNaCl 1.3.0 and ensure is compiled on linux [@sergiusens](https://github.com/sergiusens) ([#3483](https://github.com/snapcore/snapcraft/pull/3483))
-   tests: crystal 1.0.0 requires shard.lock [@sergiusens](https://github.com/sergiusens) ([#3484](https://github.com/snapcore/snapcraft/pull/3484))
-   porting conda plugin from v1 to v2 so we can use it in core20 [@ycheng](https://github.com/ycheng) ([#3457](https://github.com/snapcore/snapcraft/pull/3457))
-   project loader: ensure all key assets are utilized [@cjp256](https://github.com/cjp256) ([#3364](https://github.com/snapcore/snapcraft/pull/3364))
-   Candid bakery [@sergiusens](https://github.com/sergiusens) ([#3473](https://github.com/snapcore/snapcraft/pull/3473))
-   extensions: add core20 support to kde-neon [@sergiusens](https://github.com/sergiusens) ([#3462](https://github.com/snapcore/snapcraft/pull/3462))
-   ci: add requirements for snapcraft legacy in spread [@sergiusens](https://github.com/sergiusens) ([#3478](https://github.com/snapcore/snapcraft/pull/3478))
-   ci: reduce amount of artifacts to upload for spread [@sergiusens](https://github.com/sergiusens) ([#3476](https://github.com/snapcore/snapcraft/pull/3476))
-   godeps: set default channel to 1.15/stable [@cjp256](https://github.com/cjp256) ([#3475](https://github.com/snapcore/snapcraft/pull/3475))
-   spread tests: pin go for v1 plugin snaps [@cjp256](https://github.com/cjp256) ([#3477](https://github.com/snapcore/snapcraft/pull/3477))
-   Add flutter-stable and -beta extension variants [@MarcusTomlinson](https://github.com/MarcusTomlinson) ([#3471](https://github.com/snapcore/snapcraft/pull/3471))
-   storeapi: move http client and auth to http_clients package [@sergiusens](https://github.com/sergiusens) ([#3472](https://github.com/snapcore/snapcraft/pull/3472))
-   store: do not unnecessarily catch/rewrite exceptions [@cjp256](https://github.com/cjp256) ([#3466](https://github.com/snapcore/snapcraft/pull/3466))
-   ci: run spread store tests when secret is available [@sergiusens](https://github.com/sergiusens) ([#3470](https://github.com/snapcore/snapcraft/pull/3470))
-   gitignore: sort list [@cjp256](https://github.com/cjp256) ([#3467](https://github.com/snapcore/snapcraft/pull/3467))
-   repo: introduce DebPackage class to standardize package name parsing [@cjp256](https://github.com/cjp256) ([#3460](https://github.com/snapcore/snapcraft/pull/3460))
-   store: set auth headers when using login --with [@sergiusens](https://github.com/sergiusens) ([#3468](https://github.com/snapcore/snapcraft/pull/3468))
-   meta: add support for `kernel.yaml` for kernel snaps [@mvo5](https://github.com/mvo5) ([#3464](https://github.com/snapcore/snapcraft/pull/3464))
-   extensions: make GNOME 3.38 stable [@sergiusens](https://github.com/sergiusens) ([#3427](https://github.com/snapcore/snapcraft/pull/3427))
-   requirements: pip freeze [@sergiusens](https://github.com/sergiusens) ([#3458](https://github.com/snapcore/snapcraft/pull/3458))
-   storeapi: decouple auth and API [@sergiusens](https://github.com/sergiusens) ([#3452](https://github.com/snapcore/snapcraft/pull/3452))