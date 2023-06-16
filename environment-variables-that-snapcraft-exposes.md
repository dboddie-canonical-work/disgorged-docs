.. 7569.md

.. _environment-variables-that-snapcraft-exposes:

# Environment variables that Snapcraft exposes

**NOTE:** This table is NOT complete nor error-free, feel free to extend/fix it.

| Name & Description | Availability | Typical Values |
| :-- | :-: | :-- |
| `CFLAGS`<br>Flags to pass to the C compiler | build step? |  `-I_source_tree_dir_/stage/include` |
| `CPPFLAGS`<br>Flags to pass to the C preprocessor | build step? |  `-I_source_tree_dir_/stage/include` |
| `CXXFLAGS`<br>Flags to pass to the C++ compiler | build step? | ` -I_source_tree_dir_/stage/include` |
| `LANG`<br>Locale settings | always? | `C.UTF-8` |
| `LD_LIBRARY_PATH`<br>Dynamic Linker(man: ld.so) shared library search paths | build, stage, prime? | `:_source_tree_dir_/stage/lib:_source_tree_dir_/stage/usr/lib:_source_tree_dir_/stage/lib/_debian_multiarch_tuple_:_source_tree_dir_/stage/usr/lib/_debian_multiarch_tuple_` |
| `PATH`<br>Runtime command search PATHs, separated with colons(`:`) | build, stage, prime? | (in build step) `_source_tree_dir_/stage/usr/sbin:_source_tree_dir_/stage/usr/bin:_source_tree_dir_/stage/sbin:_source_tree_dir_/stage/bin:_source_tree_dir_/parts/_part_name_/install/usr/sbin:_source_tree_dir_/parts/_part_name_/install/usr/bin:_source_tree_dir_/parts/_part_name_/install/sbin:_source_tree_dir_/parts/_part_name_/install/bin:/home/ubuntu/bin:/home/ubuntu/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin` <br><br>(in stage/prime step) T.B.A. |
| `PERL5LIB`<br>Library search path for Perl | build, stage, prime? | `_source_tree_dir_/stage/usr/share/perl5/` |
| `PKG_CONFIG_PATH`<br>A colon-separated list of directories to search for .pc files. The default directory will always be searched after searching the path; the default is libdir/pkgconfig:datadir/pkgconfig where libdir is the libdir for pkg-config and datadir is the datadir for pkg-config when it was installed.  Refer pkg-config(1) for more info. | build? | `:_source_tree_dir_/stage/lib/pkgconfig`
| `PWD`<br>Present working directory | always | (in pull step) `_source_tree_dir_/parts/_part_name_/src`<br>(in build step) `_source_tree_dir_/parts/_part_name_/build`<br>(in stage step) `_source_tree_dir_/stage`<br>(in prime step) `_source_tree_dir_/prime` |
| `SHELL`<br>The script intepreter's path | always | `/bin/bash` |
| `SNAPCRAFT_ARCH_TRIPLET`<br>The Debian Multiarch triplet string of the target processor architecture | always? | `x86_64-linux-gnu`<br><br>`i386-linux-gnu`<br><br>(Refer [Multiarch/Tuples - Debian Wiki](https://wiki.debian.org/Multiarch/Tuples) for more) |
| `SNAPCRAFT_EXTENSIONS_DIR` | ? | `/snap/snapcraft/_snapcraft_snap_revision_/share/snapcraft/extensions` for snap build
| `SNAPCRAFT_INTERPRETER`<br>The Python interpreter that runs snapcraft | always? | `/snap/snapcraft/_snapcraft_snap_revision_/usr/bin/python3`<br>(for snap the snap distribution of Snapcraft) |
| `SNAPCRAFT_PARALLEL_BUILD_COUNT`<br>? | build step? | `4` for a 4 core/thread processor system |
| `SNAPCRAFT_PART_BUILD`<br>The build directory of the building part | build | `_source_tree_dir_/parts/_part_name_/build` |
| `SNAPCRAFT_PART_INSTALL`<br>The path of the install directory of the part | `build` step | `_source_tree_dir_/parts/_part_name_/install` |
| `SNAPCRAFT_PART_SRC`<br>The path of the src directory of the building part | build | `_source_tree_dir_/parts/_part_name_/src` |
| `SNAPCRAFT_PRIME`<br>The path of the prime directory | build, stage, prime? | `_source_tree_dir_/prime` |
| `SNAPCRAFT_PROJECT_DIR`<br>The path of the Snapcraft project's root directory, may be in a different fashion in different Snapcraft build providers | override-_step_ | `/home/_user_name_/mysnaps/_snap_name_`<br>(in `--destructive-mode`)<br>`/root/project`<br>(in LXD/Multipass build providers)
| `SNAPCRAFT_PROJECT_GRADE`<br>The `grade` of the snap | always? | `[devel|stable]`
| `SNAPCRAFT_PROJECT_NAME`<br>The `name` of the snap | always? | `_snap_name_` |
| `SNAPCRAFT_PROJECT_VERSION`<br>The `version` key's value of the snap | always? | `git` |
| `SNAPCRAFT_STAGE`<br>The absolute path of the `stage` directory | `stage` step | `_source_tree_dir_/stage` |
| `SNAPCRAFTCTL_CALL_FIFO` | ? | `/tmp/tmpXXXXXXXX/function_call` |
| `SNAPCRAFTCTL_FEEDBACK_FIFO` | ? | `/tmp/tmpXXXXXXXX/call_feedback` |

## Reference
https://github.com/snapcore/snapcraft/blob/cbd1854d9a9cfad55f7146664d3e6d15f8e3874d/snapcraft/internal/project_loader/_env.py
https://github.com/snapcore/snapcraft/blob/cbd1854d9a9cfad55f7146664d3e6d15f8e3874d/snapcraft/internal/common.py