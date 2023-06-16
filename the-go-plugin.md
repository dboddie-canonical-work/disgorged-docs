.. 8505.md

.. _the-go-plugin:

# The go plugin

The Go plugin integrates projects written in [Go](https://golang.org/). This plugin uses the common plugin keywords as well as those for [sources](/t/snapcraft-parts-metadata/8336#heading--source). For more information, see [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336).

Plugin-specific features and syntax are dependent on which [base](/t/base-snaps/11198) is being used, as outlined below:

- [base: core22](#heading--core22)
- [base: core20](#heading--core20)
- [base: core18 | core](#heading--core18)

See [Go applications](/t/go-applications/7818) for a simple example, or search [GitHub](https://github.com/search?q=path%3Asnapcraft.yaml+%22plugin%3A+go%22&type=Code) for projects already using the plugin.

> ⓘ  This is a *snapcraft* plugin. See [Snapcraft plugins](/t/snapcraft-plugins/4284) and [Supported plugins](/t/supported-plugins/8080) for further details on how plugins are used.

<h3 id='heading--core22'>base: core22</h3>

The `go` plugin in `core22` exclusively requires the use of [go.mod](https://golang.org/ref/mod).

Additionally, the build environment does not include `go` by default. To install the latest version, add `go` to a [build-snaps](/t/build-and-staging-dependencies/11451#heading--package) section for the part:

```yaml
build-snaps:
  - go
```

This plugin uses the following plugin-specific keywords:

 - **`go-buildtags`** (list of strings)
      Tags to use during the go build. Default is not to use any build tags.

Requires Snapcraft version _7.0+_.

<h3 id='heading--core20'>base: core20</h3>

The `go` plugin in `core20` exclusively requires the use of [go.mod](https://golang.org/ref/mod).

This plugin uses the following plugin-specific keywords:

 - **`go-channel`**  (string, default: latest/stable)
   The snap Store channel to install go from. If set to an empty string, go will be installed using the system's traditional package manager.

 - **`go-buildtags`** (list of strings)
      Tags to use during the go build. Default is not to use any build tags.

Requires Snapcraft version _4.0+_.

<h3 id='heading--core18'>base: core18 | core</h3>

The `go` plugin support in core and core18 can be used by Go projects using [go get](https://golang.org/pkg/cmd/go/internal/get/), the command used to grab a project's dependencies or `go mod`.

This plugin uses the following plugin-specific keywords:

 - **`go-channel`**  (string, default: latest/stable)
   The snap Store channel to install go from. If set to an empty string, go will be installed using the system's traditional package manager.

  - **`go-packages`** (list of strings)
    Go packages to fetch, these must be a "main" package.
    Dependencies are pulled in automatically by `go get`.
    Packages that are not "main" will not cause an error, but would not be useful either.
    If the package is a part of the go-importpath the local package
    corresponding to those sources will be used

 - **`go-importpath`** (string)
      This entry tells the checked out `source` to live within a certain path
      within `GOPATH`.
      This is not needed and does not affect `go-packages`.

 - **`go-buildtags`** (list of strings)
      Tags to use during the go build. Default is not to use any build tags.

Requires Snapcraft version _3.x_.