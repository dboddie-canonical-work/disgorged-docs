.. 32228.md

.. _classic-linter:

# Classic linter

The _classic_ linter is a [Snapcraft linter](/t/snapcraft-linters/32211) that is used to verify binary file parameters to ensure they are set appropriately for snaps using [classic confinement](https://forum.snapcraft.io/t/snap-confinement/6233).

The classic linter is only invoked when snap confinement is set to `classic`, or if _libc_ is staged.

- [How the classic linter helps](#heading--help)
- [Linter warnings](#heading--warnings)
- [Addressing linter issues](#heading--issues)
  - [at build time](#heading--issues-build)
  - [binary patching](#heading--issues-binary)
  - [automatic ELF patching](#heading--issues-auto)

See [Disabling linters](/t/snapcraft-linters/32211#heading--disable) for details on how to stop this linter running.

---

<h2 id='heading--help'>How the linter helps</h2>

Unlike un-snapped applications, snaps using classic confinement require dynamic executables to load shared libraries from the appropriate [base snap](t/base-snaps/11198) rather from than the host's root filesystem.

To prevent version and platform incompatibly issues, snap-based binaries need to be either built with appropriate linker parameters, or patched to allow loading shared libraries from their base snap. The classic linter helps with this by warning about libraries that need to be patched.

<h2 id='heading--warnings'>Linter warnings</h2>

The classic linter will issue a warning if the ELF binary it is testing:

1. does not use the correct dynamic linker (either from the `base` or the staged _libc_).
1. does not have an _rpath_ (run-time search path) set to a value needed to load shared library dependencies, either from the `base` or from the snap if the dependency is not part of the `base`.

[details=Example classic linter output]

```bash
Running linter: classic
Lint OK:
- classic: Snap confinement is set to classic.
Lint warnings:
- classic: usr/bin/toilet: ELF interpreter should be set to '/snap/core22/current/lib64/ld-linux-x86-64.so.2'.
- classic: usr/bin/toilet: ELF rpath should be set to '$ORIGIN/../lib/x86_64-linux-gnu:/snap/core22/current/lib/x86_64-linux-gnu'.
- classic: usr/lib/x86_64-linux-gnu/caca/libgl_plugin.so.0.0.0: ELF interpreter should be set to '/snap/core22/current/lib64/ld-linux-x86-64.so.2'.
- classic: usr/lib/x86_64-linux-gnu/caca/libgl_plugin.so.0.0.0: ELF rpath should be set to '$ORIGIN/..:/snap/core22/current/lib/x86_64-linux-gnu'.
- classic: usr/lib/x86_64-linux-gnu/caca/libx11_plugin.so.0.0.0: ELF interpreter should be set to '/snap/core22/current/lib64/ld-linux-x86-64.so.2'.
- classic: usr/lib/x86_64-linux-gnu/caca/libx11_plugin.so.0.0.0: ELF rpath should be set to '$ORIGIN/..:/snap/core22/current/lib/x86_64-linux-gnu'.
- classic: usr/lib/x86_64-linux-gnu/libcaca++.so.0.99.19: ELF interpreter should be set to '/snap/core22/current/lib64/ld-linux-x86-64.so.2'.
- classic: usr/lib/x86_64-linux-gnu/libcaca++.so.0.99.19: ELF rpath should be set to '$ORIGIN:/snap/core22/current/lib/x86_64-linux-gnu'.
- classic: usr/lib/x86_64-linux-gnu/libcaca.so.0.99.19: ELF interpreter should be set to '/snap/core22/current/lib64/ld-linux-x86-64.so.2'.
- classic: usr/lib/x86_64-linux-gnu/libcaca.so.0.99.19: ELF rpath should be set to '$ORIGIN:/snap/core22/current/lib/x86_64-linux-gnu'.
- classic: usr/lib/x86_64-linux-gnu/libslang.so.2.3.2: ELF interpreter should be set to '/snap/core22/current/lib64/ld-linux-x86-64.so.2'.
- classic: usr/lib/x86_64-linux-gnu/libslang.so.2.3.2: ELF rpath should be set to '/snap/core22/current/lib/x86_64-linux-gnu'.
```
[/details]

<h2 id='heading--issues'>Addressing issues</h2>

To address classic linter issues, the appropriate _rpath_ can be set during build time, or existing binaries can be patched to have their rpath changed.

<h3 id='heading--issues-build'>At build time</h3>

Setting _rpath_ at build time requires linker parameters to be used. The linker is typically invoked indirectly via a compiler driver; with _gcc_, for example,  case parameters can be passed to the linker using the `-Wl` option:

```bash
gcc -o foo foo.o -Wl,-rpath=\$ORIGIN/lib,--disable-new-dtags -Llib -lbar
```
A similar strategy can be used to set rpath in a [cgo](https://pkg.go.dev/cmd/cgo) binary:

```go
package main
/*
#cgo LDFLAGS: -L${SRCDIR}/lib -Wl,-rpath=\$ORIGIN/lib -Wl,--disable-new-dtags -lbar
#include "bar.h"
*/
import "C"

func main() {
    C.bar()
}
```
Linker argument  `-Wl,-dynamic-linker=...` can be used to set the ELF interpreter.

<h3 id='heading--issues-binary'>Binary patching</h3>

A snap payload may also contain pre-built ELF binaries installed from arbitrary sources (typically from the distribution archive, after installing stage packages).

In these cases, rpath must be set by modifying the existing binary using a tool such as [patchelf](https://manpages.ubuntu.com/manpages/xenial/man1/patchelf.1.html):

```bash
patchelf --force-rpath --set-rpath \$ORIGIN/lib foo
```

Or, to set the ELF interpreter, the following command can be used:

```bash
patchelf --set-interpreter /snap/core22/current/lib64/ld-linux-x86-64.so.2 foo
```

<h3 id='heading--issues-auto'>Automatic ELF file patching</h2>

Snapcraft 7.2 does not currently perform automatic ELF patching for `base: core22` classic snaps, however this feature is now available in edge. To use it, declare:
```yaml
 build-attributes:
  - enable-patchelf
```
in all parts that should have ELF binaries automatically patched.

If automatic ELF file patching is required in a stable channel, use `base: core20` until Snapcraft 7.3 is released to stable.