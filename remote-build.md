.. 14400.md

.. _remote-build:

# Remote build

There are two methods for building snaps on Canonical-hosted servers, and both are available to every snap publisher:

- **Build from GitHub**
This is a build service integrated into every publisher's [Developer Account](/t/create-a-developer-account/6760) on [snapcraft.io](https://snapcraft.io/). It works by linking a snap's GitHub repository with our Launchpad build service. See [Build from GitHub](/t/build-from-github/26004) for further details.

- **Snapcraft remote-build**
  The `snapcraft remote-build` command offloads the snap build process to the [Launchpad build farm](https://launchpad.net/builders), pushing the potentially multi-architecture snap back to your machine. See below for further details.


Remote build is a feature in [Snapcraft](/t/snapcraft-overview/8940) that enables anyone to run a multi-architecture snap build process on remote servers using [Launchpad](https://launchpad.net/).

With remote build, you can build snaps for hardware you don't have access to and free up your local machine for other tasks.

Supported build architectures are: **amd64**, **arm64**, **armhf**, **i386**, **ppc64el** and **s390x**.

> ℹ See [Creating a snap](/t/creating-a-snap/6799) for details on creating the metadata required to build a snap. For other ways to build a snap, see [Build options](/t/build-options/14250).

- [Prerequisites](#heading--prerequisites)
- [Using remote build](#heading--using)
- [Monitor a build](#heading--monitor)

---
<h2 id='heading--prerequisites'>Prerequisites</h2>

Prospective snaps need to be open source, as the code will be publicly available, and you'll need a [Launchpad account](https://login.launchpad.net/+new_account).

Build architectures can be defined within a snap's [snapcraft.yaml](/t/the-snapcraft-format/8337) using the _architectures_ keyword. To target all architectures, for example, use the following:

```yaml
architectures:
  - build-on: s390x
  - build-on: ppc64el
  - build-on: arm64
  - build-on: armhf
  - build-on: amd64
  - build-on: i386
```

If _architectures_ is not defined within snapcraft.yaml, target architectures can  be specified at build-time with the `--build-on` argument:

```bash
snapcraft remote-build --build-on=amd64,arm64
```

If no architecture is specified, remote build will default to `amd64`. For more details on how snaps handle build and run architectures, see [Architectures](/t/architectures/4972/).

<h2 id='heading--using'>Using remote build</h2>

To instantiate a remote build, use the `remote-build` argument with snapcraft:

```bash
snapcraft remote-build
```

1. You are first asked to confirm that you're happy for your local project to be transferred to a remote build server and become publicly available:

    ```no-highlight
    All data sent to remote builders will be publicly available. Are you sure
    you want to continue? [y/N]: y
    ```

   Skip the above by passing `--launchpad-accept-public-upload` to snapcraft as an extra argument.

 1. Snapcraft will now launch your default browser with an authorisation URL. The URL is also output to the terminal to allow you to copy and paste it.

    ```no-highlight
    The authorization page:
     (https://launchpad.net/+authorize-token?
    oauth_token=xxx&allow_permission=DESKTOP_INTEGRATION)
    should be opening in your browser. Use your browser to authorize
    this program to access Launchpad on your behalf.
    Waiting to hear from Launchpad about your decision...
    ```

    This prompt occurs the first time you use remote build from an new machine. Access can be enabled until you disable it, for one hour, for one day, or for one week. Alternatively, you can use the same link to disable access completely.

The remote build process will now start.

[details="Example remote-build output"]

The following is typical output for a successful single architecture remote build:

```bash
Sending build data to Launchpad... (https://<username>:<token>@git.launchpad.net/<username>/+git/snapcraft-hello-22ef03/)
If interrupted, resume with: 'snapcraft remote-build --recover'
Building snap package for amd64. This may take some time to finish.
Build status as of 2019-11-29 11:44:50.017631:
        arch=amd64      state=Needs building
Build status as of 2019-11-29 11:45:20.215169:
        arch=amd64      state=Currently building
Build status as of 2019-11-29 11:45:50.472400:
        arch=amd64      state=Currently building
Build status as of 2019-11-29 11:46:20.968422:
        arch=amd64      state=Currently building
Build status as of 2019-11-29 11:46:51.206255:
        arch=amd64      state=Uploading build
Build status as of 2019-11-29 11:47:21.871779:
        arch=amd64      state=Uploading build
Build status as of 2019-11-29 11:47:52.197560:
        arch=amd64      state=Successfully built
Snapped hello_2.10_amd64.snap
Build log available at 'hello_amd64.1.txt'
Build complete.
```
[/details]

Snapcraft waits for the build to complete before retrieving the resultant snaps, and build logs, and placing them all in your local build directory. Build time depends on the target architecture, the package size, and the availability of builder back-ends.

If your build is interrupted for any reason, it can be resumed with the `--recover` argument:

```bash
snapcraft remote-build --recover
```

<h2 id='heading--monitor'>Monitor a build</h2>

Command output from remote build will show build progress for each architecture. You can retrieve the same output from another terminal session within the build directory using the `--status` argument:

```bash
snapcraft remote-build --status
```

To see build progress outside of your command line session, open the following URL in a web browser: [https://launchpad.net/~/+snaps](https://launchpad.net/~/+snaps).

From the snap packages web page, select the build data for the job you want to monitor. The specific name for a job is part of the output from the remote-build command, such as `snapcraft-hello-22ef03`.

![Launchpad remote build management](https://assets.ubuntu.com/v1/04cd2c65-snapcraft-hello_01.png)

Selecting the build page for a build allows you to monitor the build progress for each architecture, and access the completed build log for each.

<img src="https://assets.ubuntu.com/v1/089f76d8-snapcraft-hello_02.png" alt="Launchpad remote build progress">

The Launchpad build page, and the remote build, is removed after a build terminates, regardless of whether the build was successful or not.