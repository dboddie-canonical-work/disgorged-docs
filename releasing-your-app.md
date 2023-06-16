.. 6795.md

.. _releasing-your-app:

# Releasing your app

After [creating a snap](/t/creating-a-snap/6799), you should upload it to the [Snap Store](https://snapcraft.io/store), from where it can reach a potential audience of millions, or remain _private_ if registered as such.

You will need the following:
- a free Snapcraft [developer account](/t/creating-your-developer-account/6760) account
- your own built and tested snap working with [strict](/t/snap-confinement/6233#strict) or [classic](/t/snap-confinement/6233#classic) confinement

> ⓘ If your snap requires [classic confinement](/t/snap-confinement/6233#classic), your snap will need manual approval before being released. See [Classic confinement review process](/t/process-for-reviewing-classic-confinement-snaps/1460) for further details.

## Publishing process

To get started, first [register a name](/t/registering-your-app-name/6793) for your snap in the Snap Store.

Return to the terminal and the location of your `.snap` file. You now need to authenticate the *snapcraft* command using your Snapcraft developer account credentials. This can be accomplished with the following:

```bash
snapcraft login
```

Next, upload the snap and release it into the [stable channel](/t/channels/551):

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

See [Store listing and branding](/t/store-listing-and-branding/16397) for help with making the most of a snap's store entry, and [Release management](/t/release-management/12442) for controlling which revisions appear on which channels, and to switch a snap between _Public_ and _Private_ visibility and access.

If you want to publish a snap temporarily,  to address a fix or test a new feature, see [Publish to a branch](/t/publish-to-a-branch/29544).