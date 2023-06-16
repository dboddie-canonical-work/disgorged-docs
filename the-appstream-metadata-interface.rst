.. 13050.md

.. _the-appstream-metadata-interface:

The appstream-metadata interface
================================

`AppStream <https://www.freedesktop.org/software/appstream/docs/>`__ is a metadata standard used to describe a common set software components. The ``appstream-metadata`` interface allows access to AppStream metadata from the host system.

.. note::


          See :ref:`Interface management <interface-management>` and :ref:`Supported interfaces <supported-interfaces>` for further details on how interfaces are used.

--------------

.. raw:: html

   <h2 id="the-appstream-metadata-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

**Auto-connect**: no

Requires snapd version *2.41+*.

.. raw:: html

   <h3 id="the-appstream-metadata-interface-heading-code">

Code examples

.. raw:: html

   </h3>

:ref:`Using external metadata <using-external-metadata>` describes how to access AppStream metadata.

The source code for this interface is in the *snapd* repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/appstream_metadata.go
