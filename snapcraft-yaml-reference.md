.. 4276.md

.. _snapcraft-yaml-reference:

# Snapcraft.yaml reference

This page arranges the same material found in [The snapcraft.yaml schema](/t/the-snapcraft-schema/8337) as a single page.

[quote]
 **NOTE TO EDITORS** 

This is work in progress.

This document is reference material, where possible, the attribute should include the version it was introduced or deprecated in. Links to more in-depth explanations for these resources are welcome as well as links to reasons for the deprecation.
[/quote]


| Name | Description |
|:-|:-|
| **`name`** <br> *mandatory*| The identifying name of the snap. <br> **Type:** `string` <br> Max length 40 characters. <br> It must start with an ASCII character and can only contain letters in lower case, numbers, and hyphens, and it can’t start or end with a hyphen. The name must be unique if you want to [publish to the Snap Store](/t/releasing-your-app/6795). <br> For help on choosing a name and registering it on the Snap Store, see [Registering your app name](/t/registering-your-app-name/6793). <br>  **Example:** `my-awesome-app`|
| **`title`**<br>*optional* | The canonical title of the application, displayed in the software centre graphical frontends.  <br> **Type:** `string`<br>Max length 40 characters.<br>In the legacy Snapcraft syntax (prior to the `base` key), this key is only available through the [`passthrough`](https://forum.snapcraft.io/t/using-in-development-features-in-snapcraft-yaml/5766) key.  <br>**Example:** My Awesome Application|
| **`base`** <br> *mandatory* | A snap of type [base](/t/base-snaps/11198) to be used as the execution environment for this snap.<br>**Examples:** `'core'`, `'core18'`, `'core20'`<br>This is mandatory unless the `type` parameter is  set to either `base`, `kernel`, or `snapd`. |
| **`build-base`** <br> *optional* | Used to build a [base](/t/base-snaps/11198) snap when the base is unavailable or has yet to be bootstrapped. See [Building a base snap](/t/base-snaps/11198#heading--base-snap) for details. <br>**Examples:** `'core20'`, `'core22'`<br>Requires that the `type` parameter is  set to `base`. |
| **`compression`** <br> *optional* | Sets the compression type for the snap. <br> **Type**: `string`<br> Can be `xz` or `lzo` . Defaults to `xz` when not specified. See [compression](https://forum.snapcraft.io/t/snapcraft-top-level-metadata/8334#heading--compression) for further details. |
| **`version`** <br> *mandatory* <br> unless using `adopt-info` | A user facing version to display. <br> **Type**: `string` <br> Max len. 32 chars. Needs to be wrapped with single-quotes when the value will be interpreted by the YAML parser as non-string.  This field is mandatory unless version information is provided by `adopt-info`. See [Using external metadata](/t/using-external-metadata/4642) for details.  <br> **Examples:** `'1'`, `'1.2'`, `'1.2.3'`, `git` (will be replaced by a `git describe` based version string) |
| **`contact`** <br> *optional*| Contact information for the snap. <br> **Type:** `string|list[string]` <br> Links or email address for users to contact the publisher of the snap. <br>  **Example:** `contact@product.org`|
| **`donation`** <br> *optional*| Donation information for the snap. <br> **Type:** `string|list[string]` <br> Links to provide donations for the publisher of the snap. <br>  **Example:** `https://patreon.com`|
| **`issues`** <br> *optional*| Issue tracker or bug reporting location for the snap. <br> **Type:** `string|list[string]` <br> Links or email address for users to report issues to the publisher of the snap. <br>  **Example:** `[https://github.com/org/project/issues, contact@product.org`|
| **`source-code`** <br> *optional*| Location where the source of the snap can be found. <br> **Type:** `string` <br> Repository link to where the snap project assets can be found. <br>  **Example:** `https://github.com/org/project.git`|
| **`website`** <br> *optional*| Publisher website for the snap. <br> **Type:** `string` <br> Product link for the snap. <br>  **Example:** `https://project.com`|
| **`version-script`** <br> *[deprecated](/t/deprecation-notice-10/12463)*| **Deprecated** Use `snapcraftctl set-version` [part scriptlet](/t/using-external-metadata/4642#meta-scriptlet) instead. <br> A command to determine the snap’s version string <br> **Type**: `string` <br> Runs from the working directory of the source tree root, and prints a version string to the standard output. Replaces the value of the version keyword. The version keyword is still mandatory (but ignored).|
| **`summary`** <br>*mandatory* |  Sentence summarising the snap. <br> **Type:** `string` <br> Max len. 78 characters, describing the snap in short and simple terms. <br>  **Example:** `The super cat generator` |
| **`description`** <br>*mandatory* | Multi-line description of the snap. <br> **Type:** `string` <br> A more in-depth look at what your snap does and who may find it most useful.|
| **`type`** <br>*optional* | The type of snap, implicitly set to `app` if not set.<br> **Type:** `enum` <br> For more details, see: [gadget](/t/the-gadget-snap/696), [kernel](/t/the-kernel-snap/697) and [base](/t/base-snaps/11198)| `[app|core|gadget|kernel|base]`.
| **`confinement`** <br> *optional* |  Determines if the snap should be restricted in access or not. <br> **Type:** `enum` <br> Possible values are `strict` (for no access outside of declared `interfaces` through `plugs`), `devmode` (for unrestricted access) or `classic`. For more information, refer to [Confinement](/t/snap-confinement/6233) <br> **Examples:** `strict`, or `devmode` |
| **`icon`** <br>  *optional* | Path to icon image that represents the snap in the snapcraft.io store pages and other graphical store fronts. <br> *Note that the [desktop menu](https://en.wikipedia.org/wiki/Start_menu) does not use this icon. It uses the icon in the  `.desktop` file of the application.* <br> **Type:** `string` <br> It is a relative path to a `.png` or `.svg` file from the source tree root. The [recommended](https://forum.snapcraft.io/t/restrictions-on-screenshots-and-videos-in-snap-listings/3087/24) size is 256x256 pixels. Aspect ratio needs to be 1:1. Image size can vary from 40x40 to 512x512 px and the file size should not be larger than 256 KB.<br> **Examples:** `_package_name_.svg`, or `snap/gui/logo.png`|
| **`layout`** <br>  *optional* | Modify the execution environment of a strictly-confined snap. <br> **Type:** `list[dict]` <br> Layouts are defined as a key-value map, mapping from a \<target-path\> to a layout declaration. See [Using layouts](/t/snap-layouts/7207) for more details. <br> **Examples:** `/var/lib/foo: bind: $SNAP_DATA/var/lib/foo`|
| **`license`** <br> *optional* | A license for the snap in the form of an [SPDX expression](https://spdx.org/licenses/) for the license.  In the legacy Snapcraft syntax (not using the base key), this key is only available [through the passthrough key](https://forum.snapcraft.io/t/using-in-development-features-in-snapcraft-yaml/5766).  [Currently, only SPDX 2.1 expressions are supported](https://github.com/snapcore/snapd/blob/89b5855d44686008f855582bdfd7b2bf7b1a157c/spdx/validate.go#L24), refer [snapd/licenses.go at master · snapcore/snapd](https://github.com/snapcore/snapd/blob/master/spdx/licenses.go) for accepted expressions.<br>**Type:** `string`<br>**Examples:** `GPL-3.0`, `MIT`, `Proprietary`
| **`grade`** <br>  *optional* | Defines the quality `grade` of the snap. <br> **Type:** `enum` <br> Can be either `devel` (i.e. a development version of the snap, so not to be published to the `stable` or `candidate` channels) or `stable` (i.e. a stable release or release candidate, which can be released to all channels) <br> **Example:** `[stable` or `devel`] |
| **`adopt-info`** <br>  *optional* |  Incorporate external metadata via the referenced part.  <br> Type:  `string` <br> See [Using external metadata](/t/using-external-metadata/4642) for more details. |
| **`architectures`** <br> *optional* | List of build and run architectures. <br> **Type:** `list[object]` <br> For more details, see [Architectures](/t/architectures/4972).|
| **`epoch`** <br> *optional* | Controls when users receive a configuration-breaking application release. </br> **Type:** `integer` </br> Incrementing the epoch in the new release stops old users automatically refreshing to the new version. See [Snap epochs](/t/snap-epochs/10316) for further details. |
| **`package-repositories`** <br> *optional* | Adds package repositories, including PPA-type and deb-type repositories. </br> **Type:** `list[dict]` </br> See [Snapcraft package repositories](/t/snapcraft-package-repositories/15475) for further information.|
| **`assumes`** <br> *optional* | A list of features that must be supported by the core in order for this snap to install.    For example, to make the snap only installable on certain recent version of snapd (like 2.38) you can specify: `- snapd2.38`. See [Snapcraft top-level metadata](/t/snapcraft-top-level-metadata/8334#heading--assumes) for other potential values.<br> **Type:** `list[string]` |
| **`hooks`** <br> *optional* | This top-level keyword to define a hook with a plug to access more privileges. See [Supported snap hooks](/t/supported-snap-hooks/3795) for further details. <br> **Type:** `list[string]` |
| **`passthrough`** <br>  *optional* | Attributes to passthrough to `snap.yaml` without validation from snapcraft. <br> **Type:**  `type[object]` <br> See [Using development features in snapcraft](/t/using-in-development-features-in-snapcraft-yaml/5766) for more details. |
| **apps** | A map of app-names representing entry points to run for the snap. <br> **Type:** `dict` |
|**`apps.`**<br>**`<app-name>`** | The name exposed to run a program inside the snap. <br> **Type:** `dict` <br> If `<app-name>` is the same as `name`, the program will be invoked as `app-name`. However, if they differ, the program will be exposed as `<snap-name>.<app-name>`. |
| **`apps.`**<br>**`<app-name>.`**<br> **`adapter`** <br> | Controls the creation of an env variable wrapper.<br> **Type** `enum` <br>Can be one of the following:<br>- `none`<br>- `full` _(default)_ <br> Snapcraft normally creates a wrapper holding common environment variables. Disabling this could be useful for minimal base snaps without a shell, and for statically linked binaries with no use for an environment.|
| **`apps.`**<br>**`<app-name>.`**<br> **`after`** <br> | Lists the applications a daemon is to be started after. <br> **Type** `list[string]` <br> Requires _daemon_ to be set in app metadata. See also `before` (below) and [Services and daemons](/t/services-and-daemons/12601) for more details. |
| **`apps.`** <br> **`<app-name>.`** <br>**`autostart`** <br> |  The name of the autostart `.desktop` file. <br> **Type:** `string` <br> The desktop file is placed in $SNAP_USER_DATA/.config/autostart, and the application is started using the app’s command wrapper. See  [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336#heading--autostart) for further details.|
| **`apps.`**<br>**`<app-name>.`**<br> **`before`** <br> | Lists the applications a daemon is to be started before. <br> **Type** `list[string]` <br> Requires _daemon_ to be set in app metadata. See also `after` (above) and [Services and daemons](/t/services-and-daemons/12601) for more details. |
| **`apps.`**<br>**`<app-name>.`** <br> **`command`**  | The command to run inside the snap when `<app-name>` is invoked. <br> **Type:** `string` <br> The command can be in either a snap runtime's command path, `$SNAP/usr/sbin:$SNAP/usr/bin:$SNAP/sbin:$SNAP/bin`, or an executable path relative to $SNAP. <br> If daemon is set, this will be the command to run the service. <br> Only a snap with *classic* confinement can use a relative path because `PATH` isn't modified by a wrapper in classic confinement. See [Classic confinement](/t/snap-confinement/6233) for more details. <br> **Examples:** `app-launch` for an executable placed under `$SNAP/bin`. With `classic` confinement, `bin/app-launch` for an executable placed under `$SNAP/bin`. <br> **Note:** The command must consist only of alphanumeric characters, spaces, and the following special characters: / . _ # : $ -.  If other characters are required, a wrapper script should be used for the command. <br>
| **`apps.`**<br>**`<app-name>.`**<br> **`command-chain`** <br> |  A list of commands to be executed prior to `apps.<app-name>.command`. <br> Type:  `string` <br> The list is executed, in order, before running the `apps.<app-name>.command`. <br> See [Proposal: support command-chain in apps and hooks](https://forum.snapcraft.io/t/proposal-support-command-chain-in-apps-and-hooks/6112) for more details.<br>To ensure that the Snapd distribution user running supports this feature, insert the `command-chain` value to the `assumes` property. |
| **`apps.`**<br>**`<app-name>.`**<br> **`common-id`** <br> |  An identifier to a desktop-id within an external appstream file. <br> Type:  `string` <br> See [Using external metadata](/t/using-external-metadata/4642) for more details. |
| **`apps.`**<br>**`<app-name>.`**<br> **`daemon`** <br> | Declares that `<app-name>` is a system daemon. <br> **Type:** `enum` <br> Can be one of the following: <br> - `simple`: the command is the main process. <br> - `oneshot`: the configured command will exit after completion <br> - `forking`: the configured command calls `fork()` as part of its start-up. The parent process is then expected to exit when start-up is complete <br> - `notify`: the command configured will send a signal to systemd to indicate that it's running.  See [Services and daemons](/t/services-and-daemons/12601) for further details.|
| **`apps.`**<br>**`<app-name>.`**<br> **`desktop`** <br>  | Location of the *.desktop* file. <br> **Type:** `string` <br> A path relative to the *prime* directory pointing to a desktop file, commonly used to add an application to the launch menu. Snapcraft will take care of the rest. <br> **Examples:** `usr/share/applications/my-app.desktop` and `share/applications/my-app.desktop`|
| **`apps.`**<br>**`<app-name>.`** <br> **`environment`** <br> |  A set of key-value pairs specifying the contents of environment variables. <br> **Type:** `dict` <br> Key is the environment variable name; Value is the contents of the environment variable. <br> **Example:** `LANG: C.UTF-8` |
| **`apps.`**<br>**`<app-name>.`** <br> **`extensions`** <br> |  [Extensions](/t/snapcraft-extensions/13486) to apply to this application. <br> **Type:** `list[string]` <br> **Example:** `[gnome-3-28]` |
| **`apps.`**<br>**`<app-name>.`** <br> **`install-mode`** <br> | Defines whether a freshly installed daemon is started automatically. <br> **Type:** `string` <br> Requires `daemon` to be set in _app_ metadata. Set to _disable_ to defer daemon startup to the snap,  which could then use [snapctl](/t/using-the-snapctl-tool/15002) with a [hook](/t/supported-snap-hooks/3795), for instance, or another management agent. Can be one of the following: <br> `enable` or `disable` (defaults to _enable_)|
| **`apps.`**<br>**`<app-name>.`** <br> **`plugs`** <br> |  Plugs for [interfaces](/t/interfaces/6154) to connect to. <br> **Type:** `list[string]` <br>| `<app-name>` will make these plug connections when running in `strict` `confinement` For interfaces that need *attributes*, see top-level [plugs](/t/snapcraft-top-level-metadata/8334). <br> **Example:** `[home, removable-media, raw-usb`] |
| **`apps.`**<br>**`<app-name>.`** <br> **`post-stop-command`** <br> | Runs a command from inside the snap after a service stops <br> **Type:** `string` <br> Requires `daemon` to be set in the _app_ metadata.|
| **`apps.`**<br>**`<app-name>.`** <br> **`refresh-mode`** <br> | Controls whether the daemon should be restarted during a snap refresh. <br> **Type:** `string` <br> Requires `daemon` to be set in _app_ metadata. Can be one of the following: <br> `endure` or `restart` (defaults to _restart_)|
| **`apps.`**<br>**`<app-name>.`** <br> **`slots`** <br> |  Slots for [interfaces](t/interfaces/6154) to connect to. <br> **Type:** `list[string]` <br> `<app-name>` will make these slot connections when running in `strict` confinement only. For interfaces that need *attributes*, see top-level [slots](/t/snapcraft-top-level-metadata/8334). <br> **Example:** `[home, removable-media, raw-usb`] |
| **`apps.`**<br>**`<app-name>.`** <br> **`start-timeout`** <br> | The length of time to wait for a daemon to start. <br> **Type:** `string` <br> Time duration units can be `10ns`, `10us`, `10ms`, `10s`, `10m`. Termination is via `SIGTERM` (and `SIGKILL` if that doesn't work).  <br> Requires `daemon` to be set in the _app_ metadata.|
| **`apps.`**<br>**`<app-name>.`** <br> **`stop-command`** <br> | The path to a command inside the snap to run to stop the service. <br> **Type:** `string` <br> Requires `daemon` to be set in _app_ metadata.|
| **`apps.`**<br>**`<app-name>.`** <br> **`stop-timeout`** <br> | The length of time to wait before terminating a service. <br> **Type:** `string` <br> Time duration units can be `10ns`, `10us`, `10ms`, `10s`, `10m`. Termination is via `SIGTERM` (and `SIGKILL` if that doesn't work).  <br> Requires `daemon` to be set in the _app_ metadata.|
| **`apps.`**<br>**`<app-name>.`** <br> **`timer`** <br> | Schedules when, or how often, to run a service or command. <br> **Type:** `timer string` <br> See [Timer string format](/t/timer-string-format/6562) for further details on the required syntax.  <br> Requires `daemon` to be set in the _app_ metadata. |
| **`apps.`**<br>**`<app-name>.`** <br> **`restart-condition`** <br> | Condition to restart the daemon under. <br> **Type:** `enum` <br> Defaults to `on-failure`. Other values are  `[on-failure|on-success|on-abnormal|on-abort|always|never]`. Refer to [systemd.service manual](https://www.freedesktop.org/software/systemd/man/systemd.service.html#Restart=) for details. <br>  Requires `daemon` to be set in the _app_ metadata. |
| **`apps.`**<br>**`<app-name>.`** <br> **`restart-delay`** <br> | The length of time to wait before daemon restarts. <br> **Type:** `string` <br> Time duration units can be `10ns`, `10us`, `10ms`, `10s`, `10m`.  Defaults to unset. <br> See the systemd.service manual on [RestartSec](https://www.freedesktop.org/software/systemd/man/systemd.service.html#RestartSec=) for details. Requires `daemon` to be set in the _app_ metadata.|
| **`apps.`**<br>**`<app-name>.`** <br> **`sockets`** <br> | Maps a daemon's sockets to services and activates them. <br> **Type:** `dict` <br> Requires an activated daemon socket. <br> Requires `apps.<app-name>.plugs` to declare the `network-bind` plug. |
| **`apps.`**<br>**`<app-name>.`** <br> **`socket-mode`** <br> | The mode of a socket in *octal*. <br> **Type:** `integer` |
| **`apps.`**<br>**`<app-name>.`** <br> **`listen-stream`** <br> | The socket abstract name or socket path. <br> **Type:** `string` <br> Sockets should go to a map of \<socket-name\> to objects which specify the listen-stream and (optionally) the socket-mode. <br> TCP socket syntax: `\<port\>`, `[::]:\<port\>`, `[::1]:\<port\>` and `127.0.0.1:\<port\>` <br> UNIX socket syntax: `$SNAP_DATA/\<path\>`, `$SNAP_COMMON/<path>` and `@snap.\<snap name\>.<suffix>`|
| **`apps.`**<br>**`<app-name>.`** <br> **`passthrough`** <br> | `<app-name>` attributes to pass through to `snap.yaml` without snapcraft validation. <br> **Type:** `type[object]` <br> See [Using in-development features](/t/using-in-development-features-in-snapcraft-yaml/5766) for further details. |
| **`apps.`**<br>**`<app-name>.`** <br> **`watchdog-timeout`** <br> | This value declares the service watchdog timeout.<br> **Type:** `string` <br> Time duration units can be `10ns`, `10us`, `10ms`, `10s`, `10m`. For watchdog to work, the application requires access to the _systemd_ notification socket, which can be declared by listing a daemon-notify plug in the plugs section.  <br> Requires `daemon` to be set in the _app_ metadata.|
|**`plugs`** <br>  *optional*|  A set of plugs that the snap asserts. <br> **Type:** `dict` <br> These plugs apply to all `apps` and differs from **`apps.<app-name>.plugs`** in that the type is in a `dict` rather than a `list` format, `:`(colon) must be postfixed to the interface name and shouldn't start with `- `(dash-space) |
|**`plugs.`** <br> **`<plug-name>`** <br>  *optional* | A set of attributes for a plug <br> **Type:** `dict` <br> **Example:** `read` attribute for the `home` interface |
|**`plugs.`** <br> **`<plug-name>.`** <br> **`<attribute-name>`** <br>  *optional* | Value of the attribute <br> **Type:** `string` <br> **Example:** `all` for `read` attribute of the `home` interface |
|**`slots`** <br>  *optional* | A set of slots that the snap provides. <br> **Type:** `dict`|
| | These slots apply to all the `apps` |
|**`slots.`** <br> **`<slot-name>`**  <br>  *optional* | A set of attributes of the slot <br> **Type:** `dict` |
|**`slots.`** <br> **`<slot-name>.`** <br> **`<attribute-name>`** <br>  *optional* | Value of the attribute <br> **Type:** `dict` |
| **`parts`** <br> | A set of independent building blocks. <br> **Type:** `dict` <br> These independent building blocks are known as *parts*, and consist of either code or pre-built packages. |
| **`parts.`** <br> **`<part-name>`** <br> | The name of the part building block. <br> **Type:** `dict`<br> `<part-name`> represents the specific name of a building block which can be then referenced by the command line tool (i.e. `snapcraft`). |
| **`parts.`** <br> **`<part-name>.`** <br> **`plugin`** <br> | The plugin to drive the build process. <br> **Type:** `string` <br> Every part drives its build through a plugin, this entry declares the plugin that will drive the build process for `<part-name>`. Refer to [snapcraft plugins](/t/snapcraft-plugins/4284) for more information on the available plugins and the specific attributes they add to the `parts.<part-name>.` namespace. |
| **`parts.`** <br> **`<part-name>.`** <br>**`source`** <br> | A URL or path to a source tree to build. <br> **Type:** `string` <br> This can be a local path or remote, and can refer to a directory tree, a compressed archive or a revision control repository. This entry supports additional syntax, for more information refer to [Advanced grammar](/t/snapcraft-advanced-grammar/8349). |
| **`parts.`** <br> **`<part-name>.`** <br>**`source-type`** <br> | Used when the type-of `source` entry cannot be detected.<br> **Type:** `enum` <br> Can be one of the following: `[bzr|deb|git|hg|local|mercurial|rpm|subversion|svn|tar|zip|7z]`|
| **`parts.`** <br> **`<part-name>.`** <br>**`source-checksum`** <br> | Used when `source` represents a file. <br> **Type:** `string` <br> Takes the syntax `<algorithm>/<digest>`, where `<algorithm>` can be any of: `md5`, `sha1`, `sha224`, `sha256`, `sha384`, `sha512`, `sha3_256`, `sha3_384` or `sha3_512`. When set, the source is cached for multiple uses in different snapcraft projects. |
| **`parts.`** <br> **`<part-name>.`** <br>**`source-depth`** <br> |  Depth of history for sources using version control. <br> **Type:** `integer` <br> Source repositories under version control are cloned or checked out with full history. Specifying a depth will truncate the history to the specified number of commits.|
| **`parts.`** <br> **`<part-name>.`** <br>**`source-branch`** <br> | Work on a specific branch for source repositories under version control. <br> **Type:** `string` |
| **`parts.`** <br> **`<part-name>.`** <br>**`source-commit`** <br> | Work on a specific commit for source repositories under version control. <br> **Type:** `string` |
| **`parts.`** <br> **`<part-name>.`** <br>**`source-tag`** <br> | Work on a specific tag for source repositories under version control. <br> **Type:** `string` |
| **`parts.`** <br> **`<part-name>.`** <br>**`source-subdir`** <br> | A path within the `source` to set as the working directory when building. The build will _not_ be able to access files outside of this location, such as one level up.<br> **Type:** `string` |
| **`parts.`** <br> **`<part-name>.`** <br>**`source-submodules`** <br> | Used to configure which submodules to fetch from the source tree.<br> **Type:** `dict` <br> When defined, only listed submodules are fetched. If empty, no submodules are fetched. If _submodules_ is not defined, all submodules are fetched by default. |
| **`parts.`** <br> **`<part-name>.`** <br>**`after`** <br> |  Ensures that all the `<part-name>`s listed in `after` are staged before this part begins its [lifecycle](/t/parts-lifecycle/12231#heading--steps). <br> **Type:** `list[string]` |
|  **`parts.`** <br> **`<part-name>.`** <br>**`build-environment`** | **Type:** `list[string]`<br>A list of environment variable assignments that is applied during the build step, [it is exported in order which allows for later values to override (or modify) earlier values.](https://github.com/snapcore/snapcraft/pull/2322). This entry supports additional syntax, for more information refer to [Advanced grammar](/t/snapcraft-advanced-grammar/8349). |
| **`parts.`** <br> **`<part-name>.`** <br>**`build-snaps`** <br> | A list of snap names to install that are necessary to build `<part-name>`.  <br> **Type:** `list[string]` <br> If a specific channel is required, the syntax is of the form `<snap-name>/<channel>`. This entry supports additional syntax, for more information refer to [Advanced grammar](/t/snapcraft-advanced-grammar/8349)|
| **`parts.`** <br> **`<part-name>.`** <br>**`build-packages`** <br>  | A list of packages required to build a snap. <br> **Type:** `list[string]` <br> Packages are installed using the host's package manager, such as `apt` or `dnf`, and are required for `<part-name>` to build correctly. This entry supports additional syntax, for more information refer to [Advanced grammar](/t/snapcraft-advanced-grammar/8349). <br> **Example:** `[ libssl-dev, libssh-dev, libncursesw5-dev]`
| **`parts.`** <br> **`<part-name>.`** <br>**`stage-packages`** <br> | A list of packages required at runtime by a snap. <br> **Type:** `list[string]` <br> Packages are installed using the host's package manager, such as `apt` or `dnf`, and are required by `<part-name>` to run. This entry supports additional syntax, for more information refer to [Advanced grammar](/t/snapcraft-advanced-grammar/8349). <br> **Example:** `[python-zope.interface, python-bcrypt]`|
| **`parts.`** <br> **`<part-name>.`** <br>**`stage-snaps`** <br> | A list of snaps required at runtime by a snap. <br> **Type:** `list[string]` <br> Snaps are required by \<part-name\> to run. They are fetched using `snap download`, and are unpacked into the snap being built. This entry supports additional syntax, for more information refer to [Advanced grammar](/t/snapcraft-advanced-grammar/8349).  <br> **Example:** `[hello, black/latest/edge]` |
| **`parts.`** <br> **`<part-name>.`** <br>**`organize`** <br> | A map of files to rename. <br> **Type:** `dict` <br> In the key/value pair, the key represents the path of a file inside the part and the value represents how the file is going to be staged. <br> **Example:** ` bin/snapcraftctl: bin/scriptlet-bin/snapcraftctl`.|
| **`parts.`** <br> **`<part-name>.`** <br>**`filesets`** <br> | A key to represent a group of files, or a single file.  <br> See [Snapcraft filesets](/t/snapcraft-filesets/8973) for further details. |
| **`parts.`** <br> **`<part-name>.`** <br>**`stage`** <br> | A list of files from `<part-name>` to stage. <br> **Type:** `list[string]` <br> Rules applying to the list here are the same as those of filesets. Referencing of fileset keys is done with a `$` prefixing the fileset key, which will expand with the value of such key. |
| **`parts.`** <br> **`<part-name>.`** <br> **`parse-info`** <br>|  Defines the content to adopt when using external metadata. <br> Type:  `list[string]` <br> It is a relative path to a [supported metadata file](/t/using-external-metadata/4642) from the part source, build or install directory ([SNAPCRAFT_PART_SRC, SNAPCRAFT_PART_BUILD, SNAPCRAFT_PART_INSTALL](/t/parts-lifecycle/12231#heading--parts-directories)). <br> See [Using external metadata](/t/using-external-metadata/4642) for more details. |
| **`parts.`** <br> **`<part-name>.`** <br>**`prime`** <br> | A list of files from `<part-name>` to [prime](/t/parts-lifecycle/12231#heading--steps). <br> **Type**:`list[string]` <br> Rules applying to the list here are the same as those of filesets. Referencing of fileset keys is done with a `$` prefixing the fileset key, which will expand with the value of such key. |
| **`parts.`** <br> **`<part-name>.`** <br>**`prepare`** <br>  *deprecated* | **The release of [Snapcraft 3.0](/t/release-notes-snapcraft-3-0/10704) made this key obsolete.<br>Use [`override-build`](#heading--override-build) instead.** <br> Runs a script before the plugin's [build](/t/parts-lifecycle/12231#heading--steps) step. <br> **Type:** `multiline string` <br> The script is run before the build step defined for `parts.<part-name>.plugin` starts. The working directory is the base build directory for the given part. The defined script is run with `/bin/sh` and `set -e`. <br> A set of [Environment Variables](/t/environment-variables/7983) will be available to the script. |
| **`parts.`** <br> **`<part-name>.`** <br>**`override-build`** <br>  | Replaces a plugin's default build process with a script. <br> **Type:** `multiline string` <br> The shell script defined here replaces the [build](/t/parts-lifecycle/12231#heading--steps) step of the plugin, defined in `parts.<part-name>.plugin`. The working directory is the base build directory for the given part. The defined script is run with `/bin/sh` and `set -e`.  A set of [Environment Variables](/t/environment-variables/7983) will be available to the script.|
| **`parts.`** <br> **`<part-name>.`** <br>**`override-prime`** <br>  | Replaces a plugin's default prime process with a script. <br> **Type:** `multiline string` <br> The shell script defined here replaces the [prime](/t/parts-lifecycle/12231#heading--steps) step of the plugin, defined in `parts.<part-name>.plugin`. The working directory is the base prime directory for the given part. The defined script is run with `/bin/sh` and `set -e`.  A set of [Environment Variables](/t/environment-variables/7983) will be available to the script.|
| **`parts.`** <br> **`<part-name>.`** <br>**`override-pull`** <br>  | Replaces a plugin's default pull process with a script. <br> **Type:** `multiline string` <br> The shell script defined here replaces the [pull](/t/parts-lifecycle/12231#heading--steps) step of the plugin, defined in `parts.<part-name>.plugin`. The working directory is the base pull directory for the given part. The defined script is run with `/bin/sh` and `set -e`.  A set of [Environment Variables](/t/environment-variables/7983) will be available to the script.|
| **`parts.`** <br> **`<part-name>.`** <br>**`override-stage`** <br>  | Replaces a plugin's default stage process with a script. <br> **Type:** `multiline string` <br> The shell script defined here replaces the [stage](/t/parts-lifecycle/12231#heading--steps) step of the plugin, defined in `parts.<part-name>.plugin`. The working directory is the base stage directory for the given part. The defined script is run with `/bin/sh` and `set -e`.  A set of [Environment Variables](/t/environment-variables/7983) will be available to the script.|
| **`parts.`** <br> **`<part-name>.`** <br>**`build-attributes`**   | A list of named attributes to modify the behaviour of plugins. <br> **Type:** `enum` <br> For more information, refer to [Snapcraft parts metadata](/t/snapcraft-parts-metadata/8336#heading--build-attributes). |