.. 8335.md

.. _snapcraft-app-and-service-metadata:

# Snapcraft app and service metadata

The *app* keys and values in [snapcraft.yaml](the-snapcraft-yaml-schema.md) detail the applications and services that a snap wants to expose, including how they're executed and which resources they can access.

> See [Snapcraft top-level metadata](snapcraft-top-level-metadata.md) and [Snapcraft parts metadata](snapcraft-parts-metadata.md) for details on how apps and parts are configured within *snapcraft.yaml*.

### apps

Type: `dict`

A map of `app-names` representing entry points to run for the snap.


### apps.\<app-name\>

Type: `dict`

The name exposed to run a program inside the snap.

If `<app-name>` is the same as `name`, the program will be invoked as `app-name`. However, if they differ, the program will be exposed as `<snap-name>.<app-name>`.


## Keys for apps

The following are keys that can be within **apps.<app-name>** (for example, `apps.<app-name>.daemon`):

### adapter

Type: `enum`
Can be one of the following:

- `none` (Disables the creation of an env variable wrapper.)
- `full` _(default)_

Snapcraft normally creates a wrapper holding common environment variables. Disabling this could be useful for minimal base snaps without a shell, and for statically linked binaries with no use for an environment.

<h3 id='snapcraft-app-and-service-metadata-heading--after'>after</h3>

Type: Array of  `string`

A list of applications to be started after `<app-name>`.  Applications must be part of the same snap. The order of the applications in the list has no effect on their launch order.

Requires `daemon` to be set in the _app_ metadata. See [Services and daemons](services-and-daemons.md) for details.

See also [before](#snapcraft-app-and-service-metadata-heading--before).

<h3 id='snapcraft-app-and-service-metadata-heading--autostart'>autostart<sup><a href='#snapcraft-app-and-service-metadata-heading--autostart'>⚓</a></sup></h3>

Type: `string`

Defines the name of the `.desktop` file used to start an application with the desktop session.

The desktop file is placed in `$SNAP_USER_DATA/.config/autostart`, and the application is started using the app's command wrapper (`<name>.<app>`) plus any argument present in the `Exec=` line within the _.desktop_ file.

Example: `autostart: my-chat.desktop`

See [Autostart desktop files](the-snap-format.md#snapcraft-app-and-service-metadata-heading--autostart) for an example of both the desktop file and the _Exec_ file entry.

<h3 id='snapcraft-app-and-service-metadata-heading--before'>before</h3>

Type: Array of  `string`

An ordered list of applications to be started before  `<app-name>` . Applications must be part of the same snap.

Requires `daemon` to be set in the _app_ metadata. See [Services and daemons](services-and-daemons.md) for details.

See also [after](#snapcraft-app-and-service-metadata-heading--after).

### command

Type: `string`

The command to run inside the snap when `<app-name>` is invoked.

The command can be in either a snap runtime's command path, `$SNAP/usr/sbin:$SNAP/usr/bin:$SNAP/sbin:$SNAP/bin`, or an executable path relative to $SNAP.

If daemon is set, this will be the command to run the service. Only a snap with *classic* confinement can use a relative path because `PATH` isn't modified by a wrapper in classic confinement. See [Classic confinement](snap-confinement.md) for more details.

Examples: `app-launch` for an excecutable placed under `$SNAP/bin`. With `classic` confinement, `bin/app-launch` for an executable placed under `$SNAP/bin`.

<h3 id='snapcraft-app-and-service-metadata-heading--command-chain'>command-chain</h3>

Type: Array of `string`

A list of command to be executed, in order, before the command referenced by `apps.<app-name>.command`.

See [Proposal: support command-chain in apps and hooks](https://snapcraft.io/docs/proposal-support-command-chain-in-apps-and-hooks) for further details.

To ensure that the Snapd distribution user running supports this feature, add the `command-chain` value to the `assumes` property.

### common-id

Type: `string`

An identifier to a desktop-id within an external appstream file.

See [Using external metadata](using-external-metadata.md) for more details.


### daemon

Type: `enum`

Declares that `<app-name>` is a system daemon.

Can be one of the following:
- `simple`: the command is the main process.
- `oneshot`: the configured command will exit after completion
- `forking`: the configured command calls `fork()` as part of its start-up. The parent process is then expected to exit when start-up is complete
- `notify`: the command configured will send a signal to systemd to indicate that it's running.


### desktop

Type: `string`

Location of the *.desktop* file.

A path relative to the *prime* directory pointing to a desktop file, commonly used to add an application to the launch menu. Snapcraft will take care of the rest.

Examples: `usr/share/applications/my-app.desktop` and `share/applications/my-app.desktop`


### environment

Type: `dict`

A set of key-value pairs specifying the contents of environment variables.

Key is the environment variable name; Value is the contents of the environment variable.

Example: `LANG: C.UTF-8`


<h3 id='snapcraft-app-and-service-metadata-heading--extension'>extensions</h3>

Type: `list[string] | string` (*optional*)

Snapcraft extensions enable snap developers to easily incorporate a set of common requirements into a snap, such as those to integrate an application with a desktop environment.

For further details, see [Snapcraft extensions](snapcraft-extensions.md), and see [Supported extensions](supported-extensions.md) for a full list of supported extensions.

Example: `[gnome-3-38]`

<h3 id='snapcraft-app-and-service-metadata-heading--install-mode'>install-mode</h3>

Type: `string`

Defines whether a freshly installed daemon is started automatically, or whether startup control is deferred to the snap.

If a snap was installed prior to the daemon component being added, _install-mode_ will determine whether or not the daemon is started automatically when the component is delivered via a snap update.

When disabled, the snap needs to use [snapctl](https://snapcraft.io/docs/using-the-snapctl-tool) with a [hook](supported-snap-hooks.md), or another management agent, to start the daemon.

Can be either of the following:

- `enable`: the daemon is started after being installed.
- `disable`: the daemon _will not_ be started after installation.

Defaults to `enable`.

Requires `daemon` to be set in the _app_ metadata. See [Services and daemons](services-and-daemons.md) for details.

### listen-stream

Type: `string`

The socket abstract name or socket path.

Sockets should go to a map of \<socket-name>\ to objects which specify the listen-stream and (optionally) the socket-mode.

TCP socket syntax: `<port>`, `[::]:<port>`, `[::1]:<port>` and `127.0.0.1:<port>` <br> UNIX socket syntax: `$SNAP_DATA/<path>`, `$SNAP_COMMON/<path>` and `@snap.<snap name>.<suffix>`

Example:

```yaml
      unix:
        listen-stream: $SNAP_COMMON/lxd/unix.socket
        socket-mode: 0660
```

### passthrough

Type: `type[object]`

`<app-name>` attributes to pass through to `snap.yaml` without snapcraft validation.

See [Using in-development features](using-in-development-features-in-snapcraft-yaml.md) for further details.

### plugs

Type: `list[string]`

Plugs for [interfaces](interface-management.md) to connect to.

`<app-name>` will make these plug connections when running in `strict` `confinement` For interfaces that need *attributes*, see top-level [plugs](snapcraft-top-level-metadata.md).

Example: `[home, removable-media, raw-usb`]


### post-stop-command

Type: `string`

Runs a command from inside the snap after a service stops.

Requires `daemon`  to be set in the _app_ metadata. See [Services and daemons](services-and-daemons.md) for details.

### refresh-mode

Type: `string`

Controls how the daemon or app should be treated during a snap refresh.

Can be either of the following:

- `endure`: the daemon _will not_ be restarted during a snap refresh.
- `restart`: the daemon _will_ be restarted during a snap refresh.
- `ignore-running`: the app _will not_ block a snap refresh (can only be set for apps).

Defaults to `restart`.

Requires `daemon` to be set in the _app_ metadata. See [Services and daemons](services-and-daemons.md) for details.

### restart-condition

Type: `enum`

Condition to restart the daemon under.

Defaults to `on-failure`. Other values are  `[on-failure|on-success|on-abnormal|on-abort|always|never]`. Refer to [systemd.service manual](https://www.freedesktop.org/software/systemd/man/systemd.service.html#Restart=) for details.

Requires `daemon` to be set in the _app_ metadata. See [Services and daemons](services-and-daemons.md) for details.

### slots

Type: `list[string]`

Slots for [interfaces](t/interfaces/6154) to connect to.

`<app-name>` will make these slot connections when running in `strict` confinement only. For interfaces that need *attributes*, see top-level [slots](snapcraft-top-level-metadata.md).

Example: `[home, removable-media, raw-usb`]


### sockets

Type: `dict`

Maps a daemon's sockets to services and activates them.

Requires an activated daemon socket.

Requires `apps.<app-name>.plugs` to declare the `network-bind` plug.


### socket-mode

Type: `integer`

The mode of a socket in *octal*.

### stop-command

Type: `string`

The path to a command inside the snap to run to stop the service.

Requires `daemon`  to be set in the _app_ metadata. See [Services and daemons](services-and-daemons.md) for details.

### stop-timeout

Type: `string`

The length of time to wait before terminating a service.

Time duration units can be `10ns`, `10us`, `10ms`, `10s`, `10m`. Termination is via `SIGTERM` (and `SIGKILL` if that doesn't work).


## timer

Type: `timer-string`

Schedules when, or how often, to run a service or command.

See [Timer string format](https://snapcraft.io/docs/timer-string-format) for further details on the required syntax.

Requires `daemon`  to be set in the _app_ metadata. See [Services and daemons](services-and-daemons.md) for details.