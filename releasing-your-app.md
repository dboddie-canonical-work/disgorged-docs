.. 6795.md

.. _releasing-your-app:

# Releasing your app

After [creating a snap](creating-a-snap.md), you should upload it to the [Snap Store](https://snapcraft.io/store), from where it can reach a potential audience of millions, or remain _private_ if registered as such.

You will need the following:
- a free Snapcraft [developer account](create-a-developer-account.md) account
- your own built and tested snap working with [strict](snap-confinement.md#strict) or [classic](snap-confinement.md#classic) confinement

> ⓘ If your snap requires [classic confinement](snap-confinement.md#classic), your snap will need manual approval before being released. See [Classic confinement review process](process-for-reviewing-classic-confinement-snaps.md) for further details.

## Publishing process

To get started, first [register a name](registering-your-app-name.md) for your snap in the Snap Store.

Return to the terminal and the location of your `.snap` file. You now need to authenticate the *snapcraft* command using your Snapcraft developer account credentials. This can be accomplished with the following:

```bash
snapcraft login
```

Next, upload the snap and release it into the [stable channel](https://snapcraft.io/docs/channels):

```bash
snapcraft upload --release=stable mysnap_latest_amd64.snap
```

If no errors are detected in the automated review of your upload, your app will be immediately available for installation.

[quote]
ⓘ If errors are detected, the snapcraft command will give a brief summary and guidance on how to correct each.
[/quote]

You can now test-install your snap from the Snap Store, ideally from a different testing environment to the one used to build your snap:

```bash
sudo snap install mysnap
```
Congratulations, your snap has now been released and is available on the Snap Store!

See [Store listing and branding](https://snapcraft.io/docs/store-listing-and-branding) for help with making the most of a snap's store entry, and [Release management](https://snapcraft.io/docs/release-management) for controlling which revisions appear on which channels, and to switch a snap between _Public_ and _Private_ visibility and access.

If you want to publish a snap temporarily,  to address a fix or test a new feature, see [Publish to a branch](publish-to-a-branch.md).