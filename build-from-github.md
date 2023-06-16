.. 26004.md

.. _build-from-github:

# Build from GitHub

There are two methods for building snaps on Canonical-hosted servers, and both are available to every snap publisher:

- **Snapcraft remote-build**
  The `snapcraft remote-build` command offloads the snap build process to the [Launchpad build farm](https://launchpad.net/builders), pushing the potentially multi-architecture snap back to your machine. See  [Remote build](/t/remote-build/14400) for further details.

- **Build from GitHub**
This is a build service integrated into every publisher's [Developer Account](/t/create-a-developer-account/6760) on [snapcraft.io](https://snapcraft.io/). It works by linking a snap's GitHub repository with our Launchpad build service. See below for further details.

With _Build from GitHub_, a snap is rebuilt whenever a change is merged into the main branch of its respective GitHub repository. When a build successfully completes, it's automatically released to a snap's [edge channel](/t/channels/551#heading--risk-levels).

Supported build architectures are: **amd64** , **arm64** , **armhf** , **i386** , **ppc64el** and **s390x** .

> ℹ See [Creating a snap](/t/creating-a-snap/6799) for details on creating the metadata required to build a snap. For other ways to build a snap, see [Build options](/t/build-options/14250).


- [Prerequisites](#heading--prerequisites)
- [Link to GitHub](#heading--github)
- [Select a repository](#heading--repo)
- [Monitor the build process](#heading--monitor)
- [Unlink and disable GitHub builds](#heading--unlink)

---

<h2 id='heading--prerequisites'>Prerequisites</h2>

You will need a [Developer account](/t/create-a-developer-account/6760) and accept that the source code for a prospective snap will be publicly accessible while on the build server. Projects also need to be hosted on a public [GitHub](https://github.com/) repository.

The GitHub repository must contain at least a [snapcraft.yaml](/t/the-snapcraft-format/8337) file, and the snap build from a clone of the repository. The snap name needs to be [registered](/t/registering-your-app-name/6793) with the Snap Store, and the same name needs to be declared in the _snapcraft.yaml_.

Build architectures can be defined within a snap’s [snapcraft.yaml](https://forum.snapcraft.io/t/the-snapcraft-format/8337) using the [architectures](https://forum.snapcraft.io/t/architectures/4972/) keyword. To target all architectures, for example, use the following:

```
architectures:
  - build-on: s390x
  - build-on: ppc64el
  - build-on: arm64
  - build-on: armhf
  - build-on: amd64
  - build-on: i386
```

A [snap base](/t/base-snaps/11198) of `core18` is assumed by default, unless specified otherwise. If a snap’s base doesn’t support a specified architecture, it will not be built. If no architecture is specified, snaps for all base-compatible architectures will attempt to be built.

<h2 id='heading--github'>Link to GitHub</h2>

To link your snap's GitHub repository to your snap developer account, make sure you're logged in to the developer account and go to the [My snaps](https://snapcraft.io/snaps) overview page. This is the default landing page when you log in.

Select the target snap and open its 'Builds' tab in the web UI. Use the  _GitHub login_ button to connect to GitHub. You will be asked to authorise read and write access for webhook creation, which is the mechanism used to trigger builds. Your GitHub account is now connected.

<h2 id='heading--repo'>Select a repository</h2>

With the GitHub account connected, the next step is to choose a repository.

This is accomplished by using the two drop-down menus, first to choose an organisation and then to choose the repository itself. When a repository is selected it is scanned for an appropriate _snapcraft.yaml_ configuration which, if detected, enables the _Start building_ button:

![image|677x361](https://forum-snapcraft-io.s3.dualstack.us-east-1.amazonaws.com/original/2X/b/bfc72bc1a38e19de984786d4163d27afc852fb49.png)

Click on _Start building_ to instantiate the build process and complete the linking process:

![352253a18ea8e99a914ce6697d83cddfc9d3dc89|648x146](https://forum-snapcraft-io.s3.dualstack.us-east-1.amazonaws.com/original/2X/a/adcfaf6fb18ef99655535c31875f2a980e8a9ec5.png)

<h2 id='heading--monitor'>Monitor the build process</h2>

The _Builds_ tab in the web UI will always show the build status for each supported architecture:

![image|648x380](https://forum-snapcraft-io.s3.dualstack.us-east-1.amazonaws.com/original/2X/e/e1274b75d1d4f61af27c4a4ad1a11d94b19fb27c.png)

Clicking on a build ID will take you to the status page for that specific job. This is useful if a build fails as it will contain the build log for analysis:

![image|672x396](https://forum-snapcraft-io.s3.dualstack.us-east-1.amazonaws.com/original/2X/e/e961a00115dee7d1f5a45c5b6e8be25920df079b.png)

When a build succeeds, it's automatically released to the edge channel. The release history for those builds can be viewed from the _Releases_ tab on the web UI by selecting _Launchpad_ beneath the _Revisions available to release_ heading:

![image|672x341](https://forum-snapcraft-io.s3.dualstack.us-east-1.amazonaws.com/original/2X/3/330e0d32ed9fb1496246f2db38548c417274e214.png)

See [Release management](/t/release-management/12442) for more details on how to promote and monitor release revisions and their channels.

<h2 id='heading--unlink'>Unlink and disable GitHub builds</h2>

To unlink your GitHub repo and disable automatic snap builds, navigate to the _Builds_ tab in the web UI and click on _Disconnect repo_ at the top of the page and confirm the action:

![image|665x115](https://forum-snapcraft-io.s3.dualstack.us-east-1.amazonaws.com/original/2X/f/f6af192ff385ad69a25d235f5386806a967997e1.png)

This will clear the build history on the same page, but you can still release any successful builds from the _Releases_ page of the web UI.