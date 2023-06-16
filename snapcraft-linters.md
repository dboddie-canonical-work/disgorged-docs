.. 32211.md

.. _snapcraft-linters:

# Snapcraft linters

A _linter_ is an analysis tool that checks for common errors or compatibility issues, usually automatically, or as part of some other process.

Snapcraft (from version 7.2 onwards) includes its own  linter functionality when working with snaps using the `core22` [base](base-snaps.md).

Snapcraft linters run automatically when a snap is packed unless otherwise [disabled](#snapcraft-linters-heading--disabled).

- [Available linters](#snapcraft-linters-heading--linters)
- [Disabling linters](#snapcraft-linters-heading--disable)
  -  [Ignore specific files](#snapcraft-linters-heading--disable-files)
---

<h2 id='snapcraft-linters-heading--linters'>Available linters</h2>

Snapcraft currently offers the following linters:

- **[`classic`](classic-linter.md)**: verifies binary file parameters for snaps using [classic confinement](snap-confinement.md)
- **[`library`](library-linter.md)**: verifies that no ELF file dependencies, such as libraries, are missing and that no extra libraries are included in the snap package

<h2 id='snapcraft-linters-heading--disable'>Disabling linters</h2>

Snapcraft linters run automatically when a snap is packed but specific linters can be disabled by specifying a `ignore` entry in the `lint` section of `snapcraft.yaml`:

```yaml
lint:
  ignore:
    - classic
    - library
```

The `ignore` entry must include one or more [linter names](#snapcraft-linters-heading--linters) for those linters to be disabled.

<h3 id='snapcraft-linters-heading--disable-files'>Ignore specific files</h3>

To omit specific files from a linter, add their snap location under the linter name:

```yaml
lint:
  ignore:
    - classic
    - library:
      - usr/lib/**/libfoo.so*
```

In the above example, the `classic` linter will be disabled entirely, and the `library` linter will not run for the files matching the specified file pattern.