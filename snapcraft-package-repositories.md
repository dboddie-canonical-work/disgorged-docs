.. 15475.md

.. _snapcraft-package-repositories:

# Snapcraft package repositories

When building a snap and constructing a part, package dependencies are listed as either package names or snaps for the snap’s build environment. This is covered in [Build and staging dependencies](/t/build-and-staging-dependencies/11451).

For a default [Snapcraft](/t/snapcraft-overview/8940) installation running [Multipass](https://multipass.run/), the build environment is invariably [Ubuntu 22.04 LTS](http://releases.ubuntu.com/22.04/) (Jammy Jellyfish) or [Ubuntu 20.04 LTS](http://releases.ubuntu.com/20.04/) (Focal Fossa). Consequently, dependencies are listed using their *apt* package names and are retrieved from the set of repositories officially supported by the distribution.

However, it's also possible to add your own _apt_ repositories as sources for `build-packages` and `stage-packages`, including those hosted on a PPA, the Personal Package Archive, which serves personally hosted non-standard packages.

---

- **[Adding repositories](#heading--adding)**
   - [PPA-type properties](#heading--ppa-properties)
     - [type](#heading--type)
     - [ppa](#heading--ppa)
     - [priority](#heading--priority)
   - [deb-type properties](#heading--deb-properties)
     - [architectures](#heading--architectures)
     - [components](#heading--components)
     - [formats](#heading--formats)
     - [key-id](#heading--keyid)
     - [key-server](#heading--keyserver)
     - [path](#heading--path)
     - [priority](#heading--priority)
     - [suites](#heading--suites)
     - [type](#heading--debtype)
     - [url](#heading--url)
- **[Examples](#heading--examples)**
  - [PPA repository using “ppa” property](#heading--example-pparepo)
  - [Typical apt repository with components and suites](#heading--example-aptsuites)
  - [Apt repository enabling deb sources](#heading--example-aptdeb)
  - [Absolute path repository with implied root path “/”](#heading--example-aptabspath)
  - [Absolute path repository with explicit path and formats](#heading--example-aptabspathexp)
  - [Preferring packages from a PPA](#heading--example-priority)

<h2 id='heading--adding'>Adding repositories</h2>

Third-party _apt_ repositories can be added to a snap's [snapcraft.yaml](/t/the-snapcraft-format/8337) by using the top-level `package-repositories` keyword with either a PPA-type repository, or a deb-type repository:

**[PPA-type repository](#heading--ppa-properties):**
```yaml
package-repositories:
 - type: apt
   ppa: snappy-dev/snapcraft-daily
```

**[deb-type repository](#heading--deb-properties):**
```yaml
package-repositories:
  - type: apt
    components: [main]
    suites: [xenial]
    key-id: 78E1918602959B9C59103100F1831DDAFC42E99D
    url: http://ppa.launchpad.net/snappy-dev/snapcraft-daily/ubuntu
```

As shown above, PPA-type repositories and traditional deb-type each require a different set of properties:

- [PPA-type properties](#heading--ppa-properties)
- [deb-type properties](#heading--deb-properties)

Once configured, packages provided by these repositories will become available via  `stage-packages`  and  `build-packages`.

The properties for both PPA-type and deb-type repositories are outlined below.

---

<h3 id='heading--ppa-properties'>PPA properties</h3>

The following properties are supported for PPA-type repositories:
- **[type](#heading--type)** **(required)**: The type of package-repository, only apt is currently supported.
- **[ppa](#heading--ppa)** **(required)**: PPA identifier string.
---
-    <h4 id='heading--type'>type</h4>

        - **Type:** enum[string]
        - **Description:** Specifies type of package-repository, must currently be `apt`
     -   **Examples:** `type: apt`


-    <h4 id='heading--ppa'>ppa</h4>

        -   **Type:** string
        -   **Description:** PPA shortcut string
        -   **Format:** `<ppa-owner>/<ppa-name>`
        -   **Examples:**
            -   `ppa: snappy-devs/snapcraft-daily`
            -   `ppa: mozillateam/firefox-next`

---

<h3 id='heading--deb-properties'>Deb properties</h3>

The following properties are supported for Deb-type repositories:

- **[architectures](#heading--architectures)**: List of architectures to enable, or restrict to, for this repository.
- **[components](#heading--components)**  **(required if using _suites_)**: List of _apt_ repository components to enable,  e.g. `main` , `multiverse` , `unstable`.
- **[formats](#heading--formats)**: List of _deb_ types to enable (`deb` and/or `deb-src`).
- **[key-id](#heading--keyid)** **(required)**: 40-character GPG key identifier / thumbprint.
- **[key-server](#heading--keyserver)**: Key-server to request key from.
- **[path](#heading--path)** **(required if not using _suites_ & _components_)**: Exact path to repository, relative to URL.
- **[suites](#heading--suites)** **(required if not using _path_)**: List of _apt_ suites to enable, e.g. `bionic`, `focal`.
- **[type](#heading--debtype)** **(required)**: type of package-repository. Only `apt` is currently supported.
- **[url](#heading--url)** **(required)**: apt repository URL.

---

-    <h4 id='heading--architectures'>architectures</h4>

     -   **Type:** list[string]
     -   **Description:** Architectures to enable, or restrict to, for this repository
     -   **Default:** If unspecified, architectures is assumed to match the host's architecture
     -   **Examples:**
          -   `architectures: [i386]`
          -   `architectures: [i386, amd64]`

-    <h4 id='heading--components'>components</h4>

     -   **Type:** list[string]
     -   **Description:** Apt repository components to enable: e.g. `main` , `multiverse` , `unstable`
     -   **Examples:**
         -   `components: [main]`
         -   `components: [main, multiverse, universe, restricted]`

-    <h4 id='heading--formats'>formats</h4>

     -   **Type:** list[string]
     -   **Description:** List of deb types to enable
     -   **Default:** If unspecified, format is assumed to be `deb` , i.e. `[deb]`
     -   **Examples:**
         -   `formats: [deb]`
         -   `formats: [deb, deb-src]`

-    <h4 id='heading--keyid'>key-id</h4>

     -   **Type:** string
     -   **Description:** 40 character GPG key identifier (" long-form  thumbprint" or "fingerprint")</br> If not using a key-server, Snapcraft will look for the corresponding key at: `<project>/snap/keys/<key-id[-8:]>.asc` .</br> To determine a key-id from a given key file with _gpg_, type the following: </br> `gpg --import-options show-only --import <file>`
     -   **Format:** alphanumeric, dash `-` , and underscores `_` permitted.
     -   **Examples:**
         -   `key-id: 590CA3D8E4826565BE3200526A634116E00F4C82`</br> Snapcraft will install a corresponding key at `<project>/snap/keys/E00F4C82.asc`

-    <h4 id='heading--keyserver'>key-server</h4>

     -   **Type:** string
     -   **Description:** Key server to fetch key `<key-id>` from
     -   **Default:** If unspecified, Snapcraft will attempt to fetch a specified key from [keyserver.ubuntu.com](http://keyserver.ubuntu.com/)
     -   **Format:** Key server URL supported by `gpg --keyserver`
     -   **Examples:**
         -   `key-server: keyserver.ubuntu.com`
         -   `key-server: hkp://keyserver.ubuntu.com:80`

-    <h4 id='heading--path'>path</h4>

     -   **Type:** string
     -   **Description:** Absolute path to repository (from `url` ). Cannot be used with `suites` and `components`
     -   **Format:** Path starting with `/`
     -   **Examples:**
         -   `path: /`
         -   `path: /my-repo`

-    <h4 id='heading--priority'>priority</h4>

     - _Requires Snapcraft 7.4_
     -   **Type:** enum[string] or int
     -   **Description:** Overrides the default behavior when picking the source for a particular package
     -   **Format:** `always`, `prefer` or `defer`. Alternatively an int other than 0
     -   **Notes:** string equivalencies are `always`: 1000; `prefer`: 990; `defer`: 100
     -   **Examples:**
         -   `priority: always`
         -   `priority: 1000`


-    <h4 id='heading--suites'>suites</h4>

     -   **Type:** string
     -   **Description:** Repository suites to enable
     -   **Notes:**  If your deb URL does not look like it has a suite defined, it is likely that the repository uses an absolute URL. Consider using `path`
     -   **Examples:**
         -   `suites: [xenial]`
         -   `suites: [xenial, xenial-updates]`

-    <h4 id='heading--debtype'>type</h4>

     -   **Type:** enum[string]
     -   **Description:** Specifies type of package-repository
     -   **Notes:** Must be `apt`
     -   **Examples:**
         -   `type: apt`

-    <h4 id='heading--url'>url</h4>

     -   **Type:** string
     -   **Description:** Repository URL.
     -   **Examples:**
         -   `url: http://archive.canonical.com/ubuntu`
         -   `url: https://apt-repo.com/stuff`

---

<h2 id='heading--examples'>Examples</h2>

<h3 id='heading--example-pparepo'>PPA repository using "ppa" property</h3>

```yaml
package-repositories:
  - type: apt
    ppa: snappy-dev/snapcraft-daily
```
<h3 id='heading--example-aptsuites'>Typical apt repository with components and suites</h3>

```yaml
package-repositories:
  - type: apt
    components: [main]
    suites: [xenial]
    key-id: 78E1918602959B9C59103100F1831DDAFC42E99D
    url: http://ppa.launchpad.net/snappy-dev/snapcraft-daily/ubuntu
```

<h3 id='heading--example-aptdeb'>Apt repository enabling deb sources</h3>

```yaml
package-repositories:
  - type: apt
    formats: [deb, deb-src]
    components: [main]
    suites: [xenial]
    key-id: 78E1918602959B9C59103100F1831DDAFC42E99D
    url: http://ppa.launchpad.net/snappy-dev/snapcraft-daily/ubuntu
```

<h3 id='heading--example-aptabspath'>Absolute path repository with implied root path "/"</h3>

```yaml
package-repositories:
  - type: apt
    key-id: AE09FE4BBD223A84B2CCFCE3F60F4B3D7FA2AF80
    url: https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64`
```

<h3 id='heading--example-aptabspathexp'>Absolute path repository with explicit path and formats</h3>

```yaml
package-repositories:
  - type: apt
    formats: [deb]
    path: /
    key-id: AE09FE4BBD223A84B2CCFCE3F60F4B3D7FA2AF80
    url: https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64`
```

<h3 id='heading--example-priority'>Preferring packages from a PPA</h3>

```yaml
package-repositories:
  - type: apt
    ppa: deadsnakes/ppa
    priority: always
```