.. 13123.md

.. _adding-interfaces:

# Adding interfaces

After [Defining a command](/t/defining-a-command/12060), _interfaces_ are the means by which an installed snap gets access to system resources. Interfaces that are required for normal operation are specified at snap build-time within the [app and service metadata](/t/snapcraft-app-and-service-metadata/8335) of a snap's [snapcraft.yaml](/t/creating-snapcraft-yaml/11666).

Many interfaces are automatically connected when a snap is installed, but this ability is dependent on the permissiveness of each particular interface. See [Auto-connections](/t/interface-management/6154#heading--auto-connections) for more details.

Other interfaces require the user to make a manual connection, such as [camera](t/the-camera-interface/7776) and [removable-media](/t/the-removable-media-interface/7910). Manual connections enable the user to have a complete control over what kind of access they allow.

Once published in the [Snap Store](https://snapcraft.io/store), automatic connections may be requested for manual interfaces on a case-by-case basis. For example, it may be reasonable for a photo-booth application to expect an automatic connection to the `camera` interface. Those requests are submitted and processed in the open on the Snapcraft forum. For more details on this process, see [Permission requests](/t/permission-requests/12822) .

## Plugs and slots

Interfaces are implemented as `plugs` and `slots`. A plug in one snap may connect to a slot in another and this provides access to the resources required. For example the `ohmygiraffe` snap specifies the `opengl` plug which connects to the `opengl` slot provided elsewhere - in this case by the `core` snap.

Users may view the interfaces used as a list of `plugs` and `slots` via the `snap connections` command:

```bash
$ snap connections ohmygiraffe
Interface     Plug                      Slot           Notes
network       ohmygiraffe:network       :network       -
network-bind  ohmygiraffe:network-bind  :network-bind  -
opengl        ohmygiraffe:opengl        :opengl        -
pulseaudio    ohmygiraffe:pulseaudio    :pulseaudio    -
x11           ohmygiraffe:x11           :x11           -
```

Developers specify a list of `plugs` for each application inside a snap being exposed to the host OS. Each application may have a different set of `plugs` specified. Developers should endeavour to list only the `plugs` required for normal operation of the application.

In a simplified example, a snap which contains both a server, which connects to a webcam to stream online, and a graphical application, to view the camera, may have interfaces listed as follows:

```yaml
apps:
  streamer:
    command: bin/streamer-cli
    plugs:
      - network-bind
      - camera
  frontend:
    command: bin/frontend-gui
    plugs:
      - network
      - camera
      - x11
```

> ℹ The state of a connection can be checked within a snap using the _snapctl_ utility. See [Using the snapctl tool](/t/using-the-snapctl-tool/15002) for further details.

## Common interfaces

When building a snap, its interfaces will be as unique as its application requirements. You can use the [`snappy-debug`](/t/debugging-building-snaps/6274#heading--identifying-missing-interfaces) tool to figure out which interfaces a snap needs.

The [FFmpeg](https://snapcraft.io/ffmpeg) multimedia framework, for example, needs interfaces for audio, USB cameras, network access and the desktop, [among many others](https://github.com/snapcrafters/ffmpeg/blob/master/snap/snapcraft.yaml). The game [Spelunky](https://snapcraft.io/spelunky) needs to [access](https://github.com/snapcrafters/spelunky/blob/master/snap/snapcraft.yaml) OpenGL, the desktop environment and any connected joystick.

The process of adding interfaces requires the snap developer to have a good understanding of the applications it contains, but there are certain categories of snap that require the same, or very similar, sets of interfaces.

Being familiar with these can help to speed up snap development:

- [Games interfaces](/t/games-interfaces/13125)
- [Desktop interfaces](/t/the-desktop-interfaces/2042)
- [Network interface](/t/network-interface/13124)

See [Supported interfaces](/t/supported-interfaces/7744) for the full list of interfaces available for snaps to use.