.. 12143.md

.. _iterating-over-a-build:

# Iterating over a build

When building a snap with [Snapcraft](/t/snapcraft-overview/8940), and using the [base](/t/base-snaps/11198) keyword, snapcraft by default builds within a [Multipass](https://multipass.run/) container environment tailored for the specified base.

> ℹ See [Build options](/t/build-options/14250) for an outline of alternative build environments.

To help speed up testing, it's possible to open a shell within this environment to check the state of a build, view logs, probe the value of environment variables, locate missing binaries and install missing dependencies.

The following commands enable you to step into this encapsulated environment:
-   `--shell`: builds your snap to the [lifecycle step](/t/parts-lifecycle/12231#heading--steps) prior to that specified and opens a shell into the environment (e.g. running `snapcraft prime --shell` will run up to the `stage` step and open a shell).
-   `--shell-after`: builds your snap to the [lifecycle step](/t/parts-lifecycle/12231#heading--steps) specified and opens a shell into the environment. (eg. running `snapcraft prime --shell-after` will run up to the `prime` step and then drop into a shell).
-   `--debug`, opens a shell inside the environment after an error occurs.

For example, to open a shell just before the *prime* phase, use the following command:

```bash
$ snapcraft prime --shell
Using 'snap/snapcraft.yaml': Project assets will be searched for from
the 'snap' directory.
Launching a VM.
Launched: snapcraft-test
[...]
Pulling part-test
Building part-test
Staging part-test
snapcraft-test #
```

If a build has already progressed past the stage specified, first clean the build or the part and re-build:

```bash
$ snapcraft clean
$ snapcraft build --shell
```
### Build and testing recommendations

Editing snapcraft.yaml, or the application itself, and rebuilding and re-installing each time can be time consuming, especially with larger snaps.

Here are a couple of approaches that can expedite the build process:

1) Edit *snapcraft.yaml* outside of the Snapcraft container shell environment and run `snapcraft` within the shell to continue the build.

   Run `snapcraft --debug`, rather than `snapcraft`, to  open a shell in the container environment as soon as a build error occurs.

    Remaining within the container shell environment, with access to the various staging directories, makes it easier to troubleshoot problems such as wrongly located binaries, missing dependencies, and crashing processes.

1) Use the `try` argument with both the *snapcraft* and *snap* commands.

    `$ snapcraft try`
   builds the snap and copies its *prime* directory to the current working  directory on the host system - outside of any build environment container.
    `$ sudo snap try prime`
   installs the snap by *mounting* the contents of the *prime* directory, rather than a *snap* file. This means when the contents of *prime* are edited, so too is the installed snap. Changes to interfaces in _prime/meta/snap.yaml_, however, require the snap to be removed and re-installed.
    `$ sudo snap remove <snapname>`
     remove the snap by *unmounting* the *prime* directory.

      These commands are useful when testing because files from the *prime* directory become easily viewable and modifiable without requiring a complete *snapcraft* rebuild. In-place fixes can then be migrated to the snap's snapcraft.yaml for a final build.

For more details on using the _try_ commands, see [Debug snaps with snap try](/t/debug-snaps-with-snap-try/22938) and for further help on common build issues, see [Troubleshoot snap building](/t/troubleshoot-snap-building/11938).