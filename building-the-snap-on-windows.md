.. 6829.md

.. _building-the-snap-on-windows:

# Building the snap on Windows

[quote]
 **NOTE TO EDITORS** 

This topic contributes to a new set of snap documentation. See [Proposed new documentation outline](https://forum.snapcraft.io/t/proposed-new-documentation-outline/6718) for further details.

[/quote]

Now that you have a [snapcraft.yaml](https://forum.snapcraft.io/t/creating-a-snap/6799) describing how to assemble your app and dependencies, you can build a snap.

The Microsoft Store contains an installable (WSL) Windows Subsystem for Linux containing Ubuntu 16.04.2. Once installed, users can run some Linux binaries under Windows.

[quote]
⚠ While it is possible to build, publish and release snaps using WSL, it's not currently possible to install or run them in that environment.
[/quote]

Snapcraft, the command-line tool for building snaps, is distributed in the Ubuntu repository, which is accesible under WSL. Be sure to [install WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10), choosing Ubuntu before continuing.

Once installed, run WSL from the Windows Start menu.

Next, install snapcraft:

```bash
sudo apt install snapcraft
```

Navigate to the project directory on your Windows host where the `snapcraft.yaml` file exists and run snapcraft.

```bash
snapcraft
```

[quote]
ⓘ If you are working with an Electron app, you will use the snapcraft tool for publishing to the Snap Store but not for building your snap. Electron apps do not have a snapcraft.yaml file.

[Follow this guide](https://forum.snapcraft.io/t/electron-apps/6748) to build a snap of an Electron app using electron-builder.
[/quote]

If the snap build completes successfully, you will find a `.snap` file in the same directory that you ran the snapcraft command. You can inspect its contents to ensure it contains all of your application's assets:
```
unsquashfs -l *.snap
```

### Next steps

Continue on to learn how to install, test, and publish your snap file.