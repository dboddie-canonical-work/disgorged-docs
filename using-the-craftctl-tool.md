.. 32664.md

.. _using-the-craftctl-tool:

# Using the craftctl tool

The `craftctl` tool is bundled with _snapcraft_ to help get and set metadata, and to run default actions, from scripts that [override a build step](https://forum.snapcraft.io/t/override-build-steps/4892).

It is only available when building snaps with a `core22` [base snap](/t/base-snaps/11198) or higher.

From within an override script, *craftctl* can do the following:

* **[Run the default action](#heading--run-default)**
* **[Set snap metadata](#heading--set-metadata)**
* **[Get snap metadata](#heading--get-metadata)**

<h2 id='heading--run-default'>Running the default action</h2>

When overriding a step, the default logic for that step will not be executed. Instead, the script you specify using `override-*` will run. In this script, the default logic for that step can be run with the `craftctl default` command.

For example, if you want to modify a file after pulling and before building, you can override the `pull` step, run the step using `craftctl default`, and change the sources.

```yaml
parts:
  gnome-text-editor:
    source: https://gitlab.gnome.org/GNOME/gnome-text-editor
    override-pull: |
      craftctl default
      sed -i.bak -e 's|Icon=@app_id@$|Icon=snap.gnome-text-editor.icon|g' data/org.gnome.TextEditor.desktop.in.in
```

<h2 id='heading--set-metadata'>Setting metadata</h2>

Metadata, such as the version or title of a snap, can be dynamically set within an `override-*` script using the `craftctl set <key>=<value>` command.

Replace `<key>` with the name of the value you want to change and `<value>` with what you want to change it to.

The following keys are supported:

* `version`
* `grade`

For example, if you want to set the `version` of a snap based on the `git tags` for a project, override the `pull` step with a script that first runs `craftctl default` before executing the _craftctl set version_ assignment with the _git_ command to retrieve the version information:


```yaml
adopt-info: gnome-text-editor
parts:
  gnome-text-editor:
    source: https://gitlab.gnome.org/GNOME/gnome-text-editor
    override-pull: |
      craftctl default
      craftctl set version=$(git describe --tags --abbrev=10)
```



[note type="caution" status="Caution"]
Use `adopt-info`</br>

To incorporate retrieved metadata correctly, ensure that `adopt-info` points  to the part that runs `craftctl set`. Without this, snap  metadata will not be updated.
[/note]

<h2 id='heading--get-metadata'>Getting metadata</h2>

Current metadata values can be retrieved with `craftctl get <key>`. Replace `<key>` with the name of the value to retrieve. This command supports the same keys as [Setting metadata](#heading--set-metadata).

For example, to append the git commit hash to snap version, override _stage_, run the default action, use `craftctl get version` to get the current version, and modify it:

```yaml
adopt-info: gnome-text-editor
parts:
  gnome-text-editor:
    override-stage: |
      craftctl default
      craftctl set version="$(craftctl get version)-$(git rev-parse --short HEAD)"
```