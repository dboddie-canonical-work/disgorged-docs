.. 11451.md

.. _build-and-staging-dependencies:

# Build and staging dependencies

When building a snap and constructing a [part](/t/adding-parts/11473), you commonly need to specify build and staging dependencies. Build dependencies are required for your part to successfully build or compile on the development host, while staging dependencies are required for your snap to run.

How these dependencies are identified and added is covered below.

- [Package types](#heading--package)
- [Package and snap names](#heading--package-names)
- [Identify missing packages](#heading--missing)
   - [Building](#heading--missing-building)
   - [Staging](#heading--missing-staging)
- [Removing stage package duplication](#heading--filtering)

For further help on solving build dependencies, see [Iterating over a build](/t/iterating-over-a-build/12143) for build and testing best-practices and  [Troubleshoot snap building](/t/troubleshoot-snap-building/11938) for help  resolving build errors.

---

<h2 id='heading--package'>Package types</h2>

Build and staging dependencies are added to a snap's [snapcraft.yaml](/t/the-snapcraft-format/8337) within a part definition. They can be added as standard
packages for the chosen build environment, such as _deb_ packages for Ubuntu, or as a cross-platform snap using the following _snapcraft.yaml_ keywords:

For packages:
- `build-packages`: packages required for the part to build
- `stage-packages`: packages required to run the part

For snaps:
- `build-snaps`: snaps required for the part to build.
- `stage-snaps`: snaps required to run the part

The following is a typical example of a part's *build-* and *stage-* sections for a command tool line that interacts with *git*:

```yaml
build-packages:
  - pkg-config
  - libreadline-dev
  - libncurses5-dev
build-snaps:
  - go
stage-snaps:
  - ffmpeg/latest/edge
stage-packages:
  - git
```

Snaps are downloaded from the [Snap Store](https://snapcraft.io/store) and unpacked into the snap being built.

For staged snaps, the `meta` and `snap` directories from the snap will be available as `meta.<snap-name>` and `snap.<snap-name>` for cases where assets from those locations are desired for reuse.

[note type="positive" status="Adding additional repositories"]

See [Snapcraft package repositories](https://forum.snapcraft.io/t/snapcraft-package-repositories/15475) for details on how  to add *apt* repositories as sources for `build-packages` and `stage-packages`, including those hosted on a PPA.

[/note]

<h2 id='heading--package-names'>Package and snap names</h2>

Package dependencies are listed as package names for the snap's build environment.

For a default [Snapcraft](/t/snapcraft-overview/8940) installation running [Multipass](https://multipass.run/) or [LXD](https://linuxcontainers.org/lxd/introduction/), see [Build options](/t/build-options/14250) for further details, the build environment is dependent on whatever [base snap](/t/base-snaps/11198) is being used, usually either [Ubuntu 20.04 LTS](http://releases.ubuntu.com/20.04/) (Focal Fossa) or [Ubuntu 18.04 LTS](http://releases.ubuntu.com/18.04/) (Bionic Beaver). Consequently, dependencies are listed using their respective *apt* package names.

It's also feasible to have a build environment built on Fedora for example, using Fedora packages, or those of your own host environment.

The required packages are likely to be identical to those needed to either build the project (`build-packages`) or install your project (`stage-packages`) natively. You'll often find them listed in a project's README.md, or alongside any build instructions.

Snap names are identical to the names used to install the snap outside of the build environment, and those listed by the [Snap Store](https://snapcraft.io/store).  If a specific channel is required, the syntax is of the form `<snap-name>/<channel>` (see [Channels](/t/channels/551) for more details on the syntax).

<h2 id='heading--missing'>Identifying missing packages</h2>

Working out your project's dependencies can be an iterative process, much like compiling a third-party package, with the process split into identifying the dependencies a snap needs to be built, and those required for running the resultant application.

<h3 id='heading--missing-building'>Building</h3>

1. when you have a workable framework *snapcraft.yaml* for your snap, run `snapcraft --debug` until you hit an error
1. If that error is a build dependency, use the *debug* interactive shell to work out which package is required
1. add the package to your *snapcraft.yaml* and type *snapcraft* within the build environment to see if you have the same error

A typical missing build dependency may generate an error similar to the following:

```
configure: error: can't find the Boehm GC library.  Please install it.
Failed to run 'override-build': Exit code was 1.
```

In most cases, the error will provide some indication of what needs to be installed. To resolve the error in the above example output, for instance, the Boehm GC library ( libgc) will need to be installed, and because this is the building stage, so too will its header package (libgc-dev).

If the package is unknown, it's correct name can normally be found with a search from within the build environment, or via a search engine.

<h3 id='heading--missing-staging'>Staging</h3>

After a snap has been successfully built, if snapcraft detects that the resultant executable will require further packages, it will attempt to guess these and output a list that can be copied and pasted into the snapcraft.yaml. The output will look similar to the following:

```
The 'example' part is missing libraries that are not included in the snap or base. They can be satisfied by adding the following entries to the existing stage-packages for this part:
- libxext6
- libxft2
- libxrender1
- libxss1
```

To resolve the issue, copy the output list into the staging section of the referenced part.

Another common problem is that even after snapcraft has successfully built a snap, running its executable will result in an error. The reasons for these errors are varied, but the most common is a missing library, as shown in the following example output:

```
/snap/mysnap/current/bin/mybin: error while loading shared libraries: libpaho-mqtt3a.so.1: cannot open shared object file: No such file or directory
```

The following are the most common solutions for these kind of errors:

- The required library might not be installed by the snap.
  * Add the missing package to the part's stage-packages.
- The snap app’s LD_LIBRARY_PATH var might not include the path to the missing library.
  * Update/add LD_LIBRARY_PATH environment var in snapcraft.yaml. The following, for example, adds `$SNAP/usr/lib`:
      ```yaml
      apps:
     example-app:
       [...]
       environment:
          LD_LIBRARY_PATH: $LD_LIBRARY_PATH:$SNAP/usr/lib
       ```
- The missing library might be installed by another snap and shared to this snap by a [content interface](/t/the-content-interface/1074), but the content interface is not connected.
  * Connect the snapd interface (manually for testing, or automatically for production).

<h2 id='heading--filtering'>Removing stage package duplication</h2>

Snapcraft minimises the size of a target snap by filtering out stage-package dependencies, if they are available in the base, e.g. core18.

In some cases, it may be desirable to stage a package's dependencies inside the snap, avoiding the use of the package available in the base snap. It could be that you require a more recent package to be installed, for example. To do this, explicitly add each desired package to `stage-packages` list - Snapcraft will _always_ stage any package explicitly listed.

To find the list of packages that are available in the base snap, you may find the manifest at:
`/snap/<base>/current/usr/share/snappy/dpkg.list`