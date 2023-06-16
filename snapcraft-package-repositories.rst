.. 15475.md

.. \_snapcraft-package-repositories:

Snapcraft package repositories
==============================

When building a snap and constructing a part, package dependencies are listed as either package names or snaps for the snap’s build environment. This is covered in `Build and staging dependencies <build-and-staging-dependencies.md>`__.

For a default `Snapcraft <snapcraft-overview.md>`__ installation running `Multipass <https://multipass.run/>`__, the build environment is invariably `Ubuntu 22.04 LTS <http://releases.ubuntu.com/22.04/>`__ (Jammy Jellyfish) or `Ubuntu 20.04 LTS <http://releases.ubuntu.com/20.04/>`__ (Focal Fossa). Consequently, dependencies are listed using their *apt* package names and are retrieved from the set of repositories officially supported by the distribution.

However, it’s also possible to add your own *apt* repositories as sources for ``build-packages`` and ``stage-packages``, including those hosted on a PPA, the Personal Package Archive, which serves personally hosted non-standard packages.

--------------

-  `Adding repositories <#snapcraft-package-repositories-heading--adding>`__

   -  `PPA-type properties <#snapcraft-package-repositories-heading--ppa-properties>`__

      -  `type <#snapcraft-package-repositories-heading--type>`__
      -  `ppa <#snapcraft-package-repositories-heading--ppa>`__
      -  `priority <#snapcraft-package-repositories-heading--priority>`__

   -  `deb-type properties <#snapcraft-package-repositories-heading--deb-properties>`__

      -  `architectures <#snapcraft-package-repositories-heading--architectures>`__
      -  `components <#snapcraft-package-repositories-heading--components>`__
      -  `formats <#snapcraft-package-repositories-heading--formats>`__
      -  `key-id <#snapcraft-package-repositories-heading--keyid>`__
      -  `key-server <#snapcraft-package-repositories-heading--keyserver>`__
      -  `path <#snapcraft-package-repositories-heading--path>`__
      -  `priority <#snapcraft-package-repositories-heading--priority>`__
      -  `suites <#snapcraft-package-repositories-heading--suites>`__
      -  `type <#snapcraft-package-repositories-heading--debtype>`__
      -  `url <#snapcraft-package-repositories-heading--url>`__

-  `Examples <#snapcraft-package-repositories-heading--examples>`__

   -  `PPA repository using “ppa” property <#snapcraft-package-repositories-heading--example-pparepo>`__
   -  `Typical apt repository with components and suites <#snapcraft-package-repositories-heading--example-aptsuites>`__
   -  `Apt repository enabling deb sources <#snapcraft-package-repositories-heading--example-aptdeb>`__
   -  `Absolute path repository with implied root path “/” <#snapcraft-package-repositories-heading--example-aptabspath>`__
   -  `Absolute path repository with explicit path and formats <#snapcraft-package-repositories-heading--example-aptabspathexp>`__
   -  `Preferring packages from a PPA <#snapcraft-package-repositories-heading--example-priority>`__

.. raw:: html

   <h2 id="snapcraft-package-repositories-heading--adding">

Adding repositories

.. raw:: html

   </h2>

Third-party *apt* repositories can be added to a snap’s `snapcraft.yaml <the-snapcraft-yaml-schema.md>`__ by using the top-level ``package-repositories`` keyword with either a PPA-type repository, or a deb-type repository:

`PPA-type repository <#snapcraft-package-repositories-heading--ppa-properties>`__\ **:**

.. code:: yaml

   package-repositories:
    - type: apt
      ppa: snappy-dev/snapcraft-daily

`deb-type repository <#snapcraft-package-repositories-heading--deb-properties>`__\ **:**

.. code:: yaml

   package-repositories:
     - type: apt
       components: [main]
       suites: [xenial]
       key-id: 78E1918602959B9C59103100F1831DDAFC42E99D
       url: http://ppa.launchpad.net/snappy-dev/snapcraft-daily/ubuntu

As shown above, PPA-type repositories and traditional deb-type each require a different set of properties:

-  `PPA-type properties <#snapcraft-package-repositories-heading--ppa-properties>`__
-  `deb-type properties <#snapcraft-package-repositories-heading--deb-properties>`__

Once configured, packages provided by these repositories will become available via ``stage-packages`` and ``build-packages``.

The properties for both PPA-type and deb-type repositories are outlined below.

--------------

.. raw:: html

   <h3 id="snapcraft-package-repositories-heading--ppa-properties">

PPA properties

.. raw:: html

   </h3>

The following properties are supported for PPA-type repositories: - `type <#snapcraft-package-repositories-heading--type>`__ **(required)**: The type of package-repository, only apt is currently supported. - `ppa <#snapcraft-package-repositories-heading--ppa>`__ **(required)**: PPA identifier string. — -

.. raw:: html

   <h4 id="snapcraft-package-repositories-heading--type">

type

.. raw:: html

   </h4>

::

       - **Type:** enum[string]
       - **Description:** Specifies type of package-repository, must currently be `apt`
    -   **Examples:** `type: apt`

-  

   .. raw:: html

      <h4 id="snapcraft-package-repositories-heading--ppa">

   ppa

   .. raw:: html

      </h4>

   -  **Type:** string
   -  **Description:** PPA shortcut string
   -  **Format:** ``<ppa-owner>/<ppa-name>``
   -  **Examples:**

      -  ``ppa: snappy-devs/snapcraft-daily``
      -  ``ppa: mozillateam/firefox-next``

--------------

.. raw:: html

   <h3 id="snapcraft-package-repositories-heading--deb-properties">

Deb properties

.. raw:: html

   </h3>

The following properties are supported for Deb-type repositories:

-  `architectures <#snapcraft-package-repositories-heading--architectures>`__: List of architectures to enable, or restrict to, for this repository.
-  `components <#snapcraft-package-repositories-heading--components>`__ **(required if using suites)**: List of *apt* repository components to enable, e.g. ``main`` , ``multiverse`` , ``unstable``.
-  `formats <#snapcraft-package-repositories-heading--formats>`__: List of *deb* types to enable (``deb`` and/or ``deb-src``).
-  `key-id <#snapcraft-package-repositories-heading--keyid>`__ **(required)**: 40-character GPG key identifier / thumbprint.
-  `key-server <#snapcraft-package-repositories-heading--keyserver>`__: Key-server to request key from.
-  `path <#snapcraft-package-repositories-heading--path>`__ **(required if not using suites & components)**: Exact path to repository, relative to URL.
-  `suites <#snapcraft-package-repositories-heading--suites>`__ **(required if not using path)**: List of *apt* suites to enable, e.g. ``bionic``, ``focal``.
-  `type <#snapcraft-package-repositories-heading--debtype>`__ **(required)**: type of package-repository. Only ``apt`` is currently supported.
-  `url <#snapcraft-package-repositories-heading--url>`__ **(required)**: apt repository URL.

--------------

-  

   .. raw:: html

      <h4 id="snapcraft-package-repositories-heading--architectures">

   architectures

   .. raw:: html

      </h4>

   -  **Type:** list[string]
   -  **Description:** Architectures to enable, or restrict to, for this repository
   -  **Default:** If unspecified, architectures is assumed to match the host’s architecture
   -  **Examples:**

      -  ``architectures: [i386]``
      -  ``architectures: [i386, amd64]``

-  

   .. raw:: html

      <h4 id="snapcraft-package-repositories-heading--components">

   components

   .. raw:: html

      </h4>

   -  **Type:** list[string]
   -  **Description:** Apt repository components to enable: e.g. ``main`` , ``multiverse`` , ``unstable``
   -  **Examples:**

      -  ``components: [main]``
      -  ``components: [main, multiverse, universe, restricted]``

-  

   .. raw:: html

      <h4 id="snapcraft-package-repositories-heading--formats">

   formats

   .. raw:: html

      </h4>

   -  **Type:** list[string]
   -  **Description:** List of deb types to enable
   -  **Default:** If unspecified, format is assumed to be ``deb`` , i.e. ``[deb]``
   -  **Examples:**

      -  ``formats: [deb]``
      -  ``formats: [deb, deb-src]``

-  

   .. raw:: html

      <h4 id="snapcraft-package-repositories-heading--keyid">

   key-id

   .. raw:: html

      </h4>

   -  **Type:** string
   -  **Description:** 40 character GPG key identifier (” long-form thumbprint” or “fingerprint”) If not using a key-server, Snapcraft will look for the corresponding key at: ``<project>/snap/keys/<key-id[-8:]>.asc`` . To determine a key-id from a given key file with *gpg*, type the following: ``gpg --import-options show-only --import <file>``
   -  **Format:** alphanumeric, dash ``-`` , and underscores ``_`` permitted.
   -  **Examples:**

      -  ``key-id: 590CA3D8E4826565BE3200526A634116E00F4C82``\  Snapcraft will install a corresponding key at ``<project>/snap/keys/E00F4C82.asc``

-  

   .. raw:: html

      <h4 id="snapcraft-package-repositories-heading--keyserver">

   key-server

   .. raw:: html

      </h4>

   -  **Type:** string
   -  **Description:** Key server to fetch key ``<key-id>`` from
   -  **Default:** If unspecified, Snapcraft will attempt to fetch a specified key from `keyserver.ubuntu.com <http://keyserver.ubuntu.com/>`__
   -  **Format:** Key server URL supported by ``gpg --keyserver``
   -  **Examples:**

      -  ``key-server: keyserver.ubuntu.com``
      -  ``key-server: hkp://keyserver.ubuntu.com:80``

-  

   .. raw:: html

      <h4 id="snapcraft-package-repositories-heading--path">

   path

   .. raw:: html

      </h4>

   -  **Type:** string
   -  **Description:** Absolute path to repository (from ``url`` ). Cannot be used with ``suites`` and ``components``
   -  **Format:** Path starting with ``/``
   -  **Examples:**

      -  ``path: /``
      -  ``path: /my-repo``

-  

   .. raw:: html

      <h4 id="snapcraft-package-repositories-heading--priority">

   priority

   .. raw:: html

      </h4>

   -  *Requires Snapcraft 7.4*
   -  **Type:** enum[string] or int
   -  **Description:** Overrides the default behavior when picking the source for a particular package
   -  **Format:** ``always``, ``prefer`` or ``defer``. Alternatively an int other than 0
   -  **Notes:** string equivalencies are ``always``: 1000; ``prefer``: 990; ``defer``: 100
   -  **Examples:**

      -  ``priority: always``
      -  ``priority: 1000``

-  

   .. raw:: html

      <h4 id="snapcraft-package-repositories-heading--suites">

   suites

   .. raw:: html

      </h4>

   -  **Type:** string
   -  **Description:** Repository suites to enable
   -  **Notes:** If your deb URL does not look like it has a suite defined, it is likely that the repository uses an absolute URL. Consider using ``path``
   -  **Examples:**

      -  ``suites: [xenial]``
      -  ``suites: [xenial, xenial-updates]``

-  

   .. raw:: html

      <h4 id="snapcraft-package-repositories-heading--debtype">

   type

   .. raw:: html

      </h4>

   -  **Type:** enum[string]
   -  **Description:** Specifies type of package-repository
   -  **Notes:** Must be ``apt``
   -  **Examples:**

      -  ``type: apt``

-  

   .. raw:: html

      <h4 id="snapcraft-package-repositories-heading--url">

   url

   .. raw:: html

      </h4>

   -  **Type:** string
   -  **Description:** Repository URL.
   -  **Examples:**

      -  ``url: http://archive.canonical.com/ubuntu``
      -  ``url: https://apt-repo.com/stuff``

--------------

.. raw:: html

   <h2 id="snapcraft-package-repositories-heading--examples">

Examples

.. raw:: html

   </h2>

.. raw:: html

   <h3 id="snapcraft-package-repositories-heading--example-pparepo">

PPA repository using “ppa” property

.. raw:: html

   </h3>

.. code:: yaml

   package-repositories:
     - type: apt
       ppa: snappy-dev/snapcraft-daily

.. raw:: html

   <h3 id="snapcraft-package-repositories-heading--example-aptsuites">

Typical apt repository with components and suites

.. raw:: html

   </h3>

.. code:: yaml

   package-repositories:
     - type: apt
       components: [main]
       suites: [xenial]
       key-id: 78E1918602959B9C59103100F1831DDAFC42E99D
       url: http://ppa.launchpad.net/snappy-dev/snapcraft-daily/ubuntu

.. raw:: html

   <h3 id="snapcraft-package-repositories-heading--example-aptdeb">

Apt repository enabling deb sources

.. raw:: html

   </h3>

.. code:: yaml

   package-repositories:
     - type: apt
       formats: [deb, deb-src]
       components: [main]
       suites: [xenial]
       key-id: 78E1918602959B9C59103100F1831DDAFC42E99D
       url: http://ppa.launchpad.net/snappy-dev/snapcraft-daily/ubuntu

.. raw:: html

   <h3 id="snapcraft-package-repositories-heading--example-aptabspath">

Absolute path repository with implied root path “/”

.. raw:: html

   </h3>

.. code:: yaml

   package-repositories:
     - type: apt
       key-id: AE09FE4BBD223A84B2CCFCE3F60F4B3D7FA2AF80
       url: https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64`

.. raw:: html

   <h3 id="snapcraft-package-repositories-heading--example-aptabspathexp">

Absolute path repository with explicit path and formats

.. raw:: html

   </h3>

.. code:: yaml

   package-repositories:
     - type: apt
       formats: [deb]
       path: /
       key-id: AE09FE4BBD223A84B2CCFCE3F60F4B3D7FA2AF80
       url: https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64`

.. raw:: html

   <h3 id="snapcraft-package-repositories-heading--example-priority">

Preferring packages from a PPA

.. raw:: html

   </h3>

.. code:: yaml

   package-repositories:
     - type: apt
       ppa: deadsnakes/ppa
       priority: always
