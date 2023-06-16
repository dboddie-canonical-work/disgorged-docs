.. 6753.md

.. _building-the-snap-on-linux:

# Building the snap on Linux

[quote]
 **NOTE TO EDITORS** 

This topic contributes to a new set of snap documentation. See [Proposed new documentation outline](https://forum.snapcraft.io/t/proposed-new-documentation-outline/6718) for further details.

[/quote]

Now that you have a [snapcraft.yaml](https://forum.snapcraft.io/t/creating-a-snap/6799) describing how to assemble your app and dependencies, you can build a snap.

First, [install snap support](https://forum.snapcraft.io/t/can-i-use-snaps/6735) by following the appropriate guide for your distribution. Next, install snapcraft, the command-line tool for building snaps:

```bash
sudo snap install snapcraft --classic
```

Return to the root directory of the project containing your snapcraft.yaml and run snapcraft:

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