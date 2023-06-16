.. 32285.md

.. _release-notes-snapcraft-7-2-0:

# Release notes: Snapcraft 7.2.0

The team behind Snapcraft is pleased to announce the release of [Snapcraft 7.2.0](https://github.com/snapcore/snapcraft/releases/tag/7.2.0), a major update to the tool used to build snap packages.

Among the many any other updates, fixes and additions, the following are what we consider its highlights:

* Automatic linting with the `core22` base
* Easy switching between LXD and Multipass build providers
* A new store authentication mechanism

For general details, including installation instructions, see [Snapcraft overview](https://snapcraft.io/docs/snapcraft-overview), or take a look at [Snapcraft release notes](https://snapcraft.io/docs/snapcraft-release-notes) for other *Snapcraft* releases.

## Snapcraft linting

Snapcraft now includes its own linter functionality when working with snaps using the `core22` [base](base-snaps.md). Snapcraft linters run automatically when a snap is packed, and will report any detected errors unless otherwise [disabled](snapcraft-linters.md#release-notes-snapcraft-7-2-0-heading--disabled).

The following two linters are currently supported:

* **[`classic`](classic-linter.md)**: verifies binary file parameters for snaps using [classic confinement](snap-confinement.md)
* **[`library`](library-linter.md)**: verifies that no ELF file dependencies, such as libraries, are missing

## Default provider switching

Linux users of Snapcraft can now switch the default provider (LXD) to Multipass. Do to so, run:

```
snap set snapcraft provider=multipass
```

To go back to LXD, run:

```
snap set snapcraft provider=lxd
```

See [Build providers](build-providers.md) for more details.

## Store changes

## Store

### Validation Sets

Incorrectly formatted YAML for Validation Sets, or those not completely accepted by the store, can now be interactively edited for further iteration:

[![asciicast](https://camo.githubusercontent.com/8512e6406ff4e2f4664d906da472af0456df1cd6d0928fe6afe229166c10e314/68747470733a2f2f61736369696e656d612e6f72672f612f32435572644f78645648634934417857515a4634334d5248512e737667)](https://asciinema.org/a/2CUrdOxdVHcI4AxWQZF43MRHQ)

### On Prem Store

Supported commands are:

* upload
* release
* list-revisions
* close
* status
* login
* export-login
* logout
* whoami

To work with a deployed on premises store, the following must be set:

* `STORE_DASHBOARD_URL=http[s]://<store-IP>/publisher`
* `STORE_UPLOAD_URL=http[s]://<store-IP>`
* `SNAPCRAFT_STORE_AUTH=onprem`

### Credentials Format

Snapcraft 7.2 now outputs a new standard (to the tools that require it) export login. This format is usable by Ubuntu Image and snapd.

Existing exported credentials remain compatible, however these *newly* exported tokens are not backwards compatible with versions lower than Snapcraft 7.2.0

## Full list of changes

The following is the complete list of features and issues worked on for 7.2.0. See The [Snapcraft 7.2.0 GitHub release](https://github.com/snapcore/snapcraft/releases/tag/7.2.0) for further details.

[details=List of changes for Snapcraft 7.2.0]
-   linters: add linting infrastructure by [@cmatsuoka](https://github.com/cmatsuoka) in [#3847](https://github.com/snapcore/snapcraft/pull/3847)
-   lint: lint legacy code with isort by [@mr-cal](https://github.com/mr-cal) in [#3852](https://github.com/snapcore/snapcraft/pull/3852)
-   lint: lint legacy code with black by [@mr-cal](https://github.com/mr-cal) in [#3853](https://github.com/snapcore/snapcraft/pull/3853)
-   lint: lint legacy code with flake8 by [@mr-cal](https://github.com/mr-cal) in [#3854](https://github.com/snapcore/snapcraft/pull/3854)
-   linters: add classic confinement linter by [@cmatsuoka](https://github.com/cmatsuoka) in [#3849](https://github.com/snapcore/snapcraft/pull/3849)
-   Release/7.1 merge by [@sergiusens](https://github.com/sergiusens) in [#3861](https://github.com/snapcore/snapcraft/pull/3861)
-   store: move package out of commands by [@sergiusens](https://github.com/sergiusens) in [#3862](https://github.com/snapcore/snapcraft/pull/3862)
-   whoami command: account for missing expires by [@sergiusens](https://github.com/sergiusens) in [#3863](https://github.com/snapcore/snapcraft/pull/3863)
-   Add binding for amdgpu.ids by [@sergio-costas](https://github.com/sergio-costas) in [#3859](https://github.com/snapcore/snapcraft/pull/3859)
-   names command: move presentation logic to StoreClientCLI by [@sergiusens](https://github.com/sergiusens) in [#3864](https://github.com/snapcore/snapcraft/pull/3864)
-   plugins command: support for core22 by [@sergiusens](https://github.com/sergiusens) in [#3870](https://github.com/snapcore/snapcraft/pull/3870)
-   meta: get content provider dirs from snap metadata by [@cmatsuoka](https://github.com/cmatsuoka) in [#3871](https://github.com/snapcore/snapcraft/pull/3871)
-   linters: add missing library linter by [@cmatsuoka](https://github.com/cmatsuoka) in [#3872](https://github.com/snapcore/snapcraft/pull/3872)
-   lint: lint legacy code with black by [@mr-cal](https://github.com/mr-cal) in [#3865](https://github.com/snapcore/snapcraft/pull/3865)
-   meta: fix content plug detection by [@cmatsuoka](https://github.com/cmatsuoka) in [#3874](https://github.com/snapcore/snapcraft/pull/3874)
-   store: on prem base client by [@sergiusens](https://github.com/sergiusens) in [#3880](https://github.com/snapcore/snapcraft/pull/3880)
-   extensions: replace execs with source by [@sergio-costas](https://github.com/sergio-costas) in [#3869](https://github.com/snapcore/snapcraft/pull/3869)
-   ua: add support to ua token management by [@cmatsuoka](https://github.com/cmatsuoka) in [#3883](https://github.com/snapcore/snapcraft/pull/3883)
-   store: initial support for an onprem store by [@sergiusens](https://github.com/sergiusens) in [#3885](https://github.com/snapcore/snapcraft/pull/3885)
-   store: support status for an onprem store by [@sergiusens](https://github.com/sergiusens) in [#3887](https://github.com/snapcore/snapcraft/pull/3887)
-   Hotfix/7.1.2 merge by [@sergiusens](https://github.com/sergiusens) in [#3888](https://github.com/snapcore/snapcraft/pull/3888)
-   Write passthrough to meta data and add some missing fields by [@valentindavid](https://github.com/valentindavid) in [#3882](https://github.com/snapcore/snapcraft/pull/3882)
-   DT-500 Fix Cups for Gtk support in Gnome-42 by [@sergio-costas](https://github.com/sergio-costas) in [#3867](https://github.com/snapcore/snapcraft/pull/3867)
-   ua: specify and enable ua services by [@cmatsuoka](https://github.com/cmatsuoka) in [#3886](https://github.com/snapcore/snapcraft/pull/3886)
-   ua: enable ua services in legacy by [@cmatsuoka](https://github.com/cmatsuoka) in [#3890](https://github.com/snapcore/snapcraft/pull/3890)
-   store: support close for an on prem store by [@sergiusens](https://github.com/sergiusens) in [#3892](https://github.com/snapcore/snapcraft/pull/3892)
-   Merge 7.1.3 release by [@sergiusens](https://github.com/sergiusens) in [#3894](https://github.com/snapcore/snapcraft/pull/3894)
-   Hotfix/7.1.4 merge by [@sergiusens](https://github.com/sergiusens) in [#3900](https://github.com/snapcore/snapcraft/pull/3900)
-   config: add snap config model by [@mr-cal](https://github.com/mr-cal) in [#3898](https://github.com/snapcore/snapcraft/pull/3898)
-   store: on prem support for list-revisions by [@sergiusens](https://github.com/sergiusens) in [#3901](https://github.com/snapcore/snapcraft/pull/3901)
-   commands: update lifecycle docstrings by [@cmatsuoka](https://github.com/cmatsuoka) in [#3902](https://github.com/snapcore/snapcraft/pull/3902)
-   providers: choose default provider from snap config for core 22 by [@mr-cal](https://github.com/mr-cal) in [#3899](https://github.com/snapcore/snapcraft/pull/3899)
-   providers: choose legacy default provider from snap config by [@mr-cal](https://github.com/mr-cal) in [#3903](https://github.com/snapcore/snapcraft/pull/3903)
-   providers: pass http-proxy and https-proxy to craft-providers by [@mr-cal](https://github.com/mr-cal) in [#3906](https://github.com/snapcore/snapcraft/pull/3906)
-   parts: minor refactoring in instance log capture by [@cmatsuoka](https://github.com/cmatsuoka) in [#3905](https://github.com/snapcore/snapcraft/pull/3905)
-   tests: minor refactoring in shell/shell-after tests by [@cmatsuoka](https://github.com/cmatsuoka) in [#3904](https://github.com/snapcore/snapcraft/pull/3904)
-   parts: use part validator from craft-parts by [@cmatsuoka](https://github.com/cmatsuoka) in [#3909](https://github.com/snapcore/snapcraft/pull/3909)
-   tests unit: add for on prem store list-revisions by [@sergiusens](https://github.com/sergiusens) in [#3908](https://github.com/snapcore/snapcraft/pull/3908)
-   store: improve error message for 401 error by [@sergiusens](https://github.com/sergiusens) in [#3907](https://github.com/snapcore/snapcraft/pull/3907)
-   unit tests: minor improvement to fixture usage by [@sergiusens](https://github.com/sergiusens) in [#3910](https://github.com/snapcore/snapcraft/pull/3910)
-   requirements: update craft-providers to 1.4.2 by [@mr-cal](https://github.com/mr-cal) in [#3911](https://github.com/snapcore/snapcraft/pull/3911)
-   discovery.py: correct comment, "extensions" should say "plugins" by [@rpjday](https://github.com/rpjday) in [#3912](https://github.com/snapcore/snapcraft/pull/3912)
-   build(deps): bump oauthlib from 3.2.0 to 3.2.1 by [@dependabot](https://github.com/dependabot) in [#3914](https://github.com/snapcore/snapcraft/pull/3914)
-   legacy: install unpinned build packages by [@cmatsuoka](https://github.com/cmatsuoka) in [#3915](https://github.com/snapcore/snapcraft/pull/3915)
-   cli: move remote build out of legacy by [@sergiusens](https://github.com/sergiusens) in [#3919](https://github.com/snapcore/snapcraft/pull/3919)
-   schema: allow the gnome extension by [@sergiusens](https://github.com/sergiusens) in [#3920](https://github.com/snapcore/snapcraft/pull/3920)
-   store: correctly logout when credentials are invalid for legacy by [@sergiusens](https://github.com/sergiusens) in [#3921](https://github.com/snapcore/snapcraft/pull/3921)
-   providers: move `get_instance_name()` to providers.py by [@mr-cal](https://github.com/mr-cal) in [#3926](https://github.com/snapcore/snapcraft/pull/3926)
-   requirements: update craft-parts to 1.14.2 by [@cmatsuoka](https://github.com/cmatsuoka) in [#3924](https://github.com/snapcore/snapcraft/pull/3924)
-   providers: move `get_command_environment()` to providers.py by [@mr-cal](https://github.com/mr-cal) in [#3927](https://github.com/snapcore/snapcraft/pull/3927)
-   build(deps): bump protobuf from 3.20.1 to 3.20.2 by [@dependabot](https://github.com/dependabot) in [#3923](https://github.com/snapcore/snapcraft/pull/3923)
-   test_pip.py: correct typo "enviroment" consistently so things keep wo... by [@rpjday](https://github.com/rpjday) in [#3916](https://github.com/snapcore/snapcraft/pull/3916)
-   tests: mock and test provider calls from lifecycle.py by [@mr-cal](https://github.com/mr-cal) in [#3928](https://github.com/snapcore/snapcraft/pull/3928)
-   providers: move mount logic to lifecycle.py by [@mr-cal](https://github.com/mr-cal) in [#3930](https://github.com/snapcore/snapcraft/pull/3930)
-   providers: refactor clean_project_environments by [@mr-cal](https://github.com/mr-cal) in [#3929](https://github.com/snapcore/snapcraft/pull/3929)
-   providers: refactor `launched_environment()` by [@mr-cal](https://github.com/mr-cal) in [#3932](https://github.com/snapcore/snapcraft/pull/3932)
-   providers: install snaps and packages via craft-providers API by [@mr-cal](https://github.com/mr-cal) in [#3933](https://github.com/snapcore/snapcraft/pull/3933)
-   providers: deprecate SnapcraftBuilddBaseConfiguration by [@mr-cal](https://github.com/mr-cal) in [#3934](https://github.com/snapcore/snapcraft/pull/3934)
-   providers: refactor `capture_logs_from_instance()` by [@mr-cal](https://github.com/mr-cal) in [#3935](https://github.com/snapcore/snapcraft/pull/3935)
-   commands: make help message consistent by [@nteodosio](https://github.com/nteodosio) in [#3917](https://github.com/snapcore/snapcraft/pull/3917)
-   tests: add unit test for `capture_logs_from_instance()` by [@mr-cal](https://github.com/mr-cal) in [#3937](https://github.com/snapcore/snapcraft/pull/3937)
-   providers: move `confirm_with_user()` call to providers.py ([#91](https://github.com/snapcore/snapcraft/pull/91)) by [@mr-cal](https://github.com/mr-cal) in [#3938](https://github.com/snapcore/snapcraft/pull/3938)
-   linters: allow ignoring files per-linter by [@tigarmo](https://github.com/tigarmo) in [#3931](https://github.com/snapcore/snapcraft/pull/3931)
-   providers: move `get_provider()` to providers.py by [@mr-cal](https://github.com/mr-cal) in [#3940](https://github.com/snapcore/snapcraft/pull/3940)
-   command: update edit-validation-sets to craft-cli by [@sergiusens](https://github.com/sergiusens) in [#3939](https://github.com/snapcore/snapcraft/pull/3939)
-   lint: support the existence of 'venv' by [@tigarmo](https://github.com/tigarmo) in [#3941](https://github.com/snapcore/snapcraft/pull/3941)
-   commands: allow re-editing validation sets on error by [@sergiusens](https://github.com/sergiusens) in [#3942](https://github.com/snapcore/snapcraft/pull/3942)
-   providers: use new craft-providers interface by [@mr-cal](https://github.com/mr-cal) in [#3943](https://github.com/snapcore/snapcraft/pull/3943)
-   tests: fix electron spread test by [@mr-cal](https://github.com/mr-cal) in [#3944](https://github.com/snapcore/snapcraft/pull/3944)
-   requirements: craft-store 2.3.0 for new credentials by [@sergiusens](https://github.com/sergiusens) in [#3945](https://github.com/snapcore/snapcraft/pull/3945)
-   fix: confirm provider install when using experiental extension by [@Guillaumebeuzeboc](https://github.com/Guillaumebeuzeboc) in [#3866](https://github.com/snapcore/snapcraft/pull/3866)
-   requirements: update by [@sergiusens](https://github.com/sergiusens) in [#3948](https://github.com/snapcore/snapcraft/pull/3948)
[/details]