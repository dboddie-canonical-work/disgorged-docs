.. 32229.md

.. _library-linter:

# Library linter

The _library_ linter is a [Snapcraft linter](/t/snapcraft-linters/32211) that is used to verify whether any  ELF file dependencies, typically libraries, are missing from a snap.  It also verifies if any libraries are included in a snap but are not used.

- [How the library linter helps](#heading--help)
- [Linter warnings](#heading--warnings)
  - [Example](#heading--warnings-example)
- [Addressing linter issues](#heading--issues)

See [Disabling linters](/t/snapcraft-linters/32211#heading--disable) for details on how to stop this linter running.

---

<h2 id='heading--help'>How the linter helps</h2>

If a snapped application depends on libraries neither provided by the [base](/t/base-snaps/11198) system, nor included as a dependency, the snap package may execute in an incorrect or unpredictable way. The library linter issues a warning if a missing dependency is detected.

Snap package size can be reduced by removing extra libraries that are not used by the applications in the snap.  The library linter issues a warning if unused libraries are detected.

<h2 id='heading--warnings'>Linter warnings</h2>

The library linter will issue a warning if:

- ELF dependencies are detected as missing from the snap package.
- Libraries not used by an ELF file in the snap package are detected.

<h3 id='heading--warnings-example'>Example</h3>

The example below shows two missing libraries (`libcaca` and `libslang`) and one unused library (`libpng16`).

```log
Running linter: library
Lint warnings:
- library: my-app: missing dependency 'libcaca.so.0'.
- library: my-app: missing dependency 'libslang.so.2'.
- library: libpng16.so.16: unused library 'usr/lib/x86_64-linux-gnu/libpng16.so.16.37.0'.
```

<h2 id='heading--issues'>Addressing issues</h2>

To address library linter issues, packages containing any missing libraries need to be added to the list of `stage-packages`. Unused libraries can be removed from `stage-packages`.  See [Build and staging dependencies](/t/build-and-staging-dependencies/11451) for further details.