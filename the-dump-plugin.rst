.. 8007.md

.. \_the-dump-plugin:

The dump plugin
===============

This plugin dumps the content from a specified source.

You can specify various details about such a source using `source keywords <snapcraft-parts-metadata.md#the-dump-plugin-heading--source>`__, such as ``source`` and ``source-type``.

This plugin uses also `common plugin keywords <snapcraft-parts-metadata.md>`__. Such keywords can, for example, be useful when the dumped content needs to be mangled or organised in some way. Using keywords such as ``filesets``, ``stage``, ``snap`` and ``organize`` can be useful in such cases.

For example:

.. code:: yaml

   parts:
     my-part:
       source: local-source/
       plugin: dump
       organize:
         '*.png' : images/
         launch.wrapper: usr/bin/launcher
       prime:
         - -README*
     remote-part:
       source: https://remote-resource.org/cool-package.deb
       source-type: deb

See `source keywords <snapcraft-parts-metadata.md#the-dump-plugin-heading--source>`__ and `common plugin keywords <snapcraft-plugins.md>`__ for more informations.

For more examples, click here to find `GitHub <https://github.com/search?o=desc&q=path%3Asnapcraft.yaml+%22plugin%3A+dump%22+&s=indexed&type=Code&utf8=%E2%9C%93>`__ projects already using this plugin.

   ⓘ This is a *snapcraft* plugin. See `Snapcraft plugins <snapcraft-plugins.md>`__ and `Supported plugins <supported-plugins.md>`__ for further details on how plugins are used.