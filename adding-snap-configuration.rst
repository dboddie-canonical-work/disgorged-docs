.. 15246.md

.. _adding-snap-configuration:

Adding snap configuration
=========================

A snap can process modifiable options that allow its user to change application settings, and the behaviour of applications, within the snap.

The `Nextcloud snap <https://snapcraft.io/nextcloud>`__, for example, allows users to `configure <https://github.com/nextcloud/nextcloud-snap#configuration>`__ the hostname, ports, php memory limit, using the ``snap set`` command:

.. code:: bash

   sudo snap set nextcloud ports.http=81

This page describes how a snap developer can add configuration options, such as the above, to an already working `snapcraft.yaml </t/creating-snapcraft-yaml/11666>`__:

-  `Interpreting options <heading--interpreting_>`__
-  `Default values <heading--default_>`__
-  `Nested values <heading--nested_>`__
-  `Example implementation <heading--example_>`__

   -  `Management script <heading--management_>`__
   -  `Default-configure script <heading--default-configure_>`__
   -  `Configure hook script <heading--configure_>`__
   -  `Wrapper script <heading--wrapper_>`__
   -  `Snapcraft.yaml <heading--snapcraft_>`__

.. note::
          ℹ For more information on how to change a snap’s configuration, rather than adding the functionality to a snap, see `Managing snap configuration </t/managing-snap-configuration/510>`__.

--------------


.. _heading--interpreting:

Interpreting options
--------------------

Internally, snaps view and change their configuration using the `snapctl tool </t/using-the-snapctl-tool/15002>`__ and its ``get``, ``set`` and ``unset`` arguments.

Configuration options are not defined when a snap is created because any (valid) option name is accepted. Instead, any set values need to be interpreted and converted into an action by the snap developer.

A snap developer is free to implement this process however they prefer, however it’s most commonly accomplished with a purpose built script or function for each option, as defined by a snap’s `snapcraft.yaml </t/creating-snapcraft-yaml/11666>`__ and its associated scripts and `hooks </t/supported-snap-hooks/3795>`__.

Permitted values should then be documented in the snap description so that users know which values are supported.


.. _heading--default:

Default values
--------------

The snap daemon has no concept of *default values* for configuration options. Actions for these values need to be implemented by the snap developer using the ```configure`` hook </t/supported-snap-hooks/3795#heading--the-configure-hook>`__.

When a user resets a configuration option with ``snap unset``, or installs a snap, the *configure hook* is run and the snap developer can therefore use this hook to check when these values are unset and, if so, use ``snapctl set`` to restore that option to its default value.

Setting these values explicitly is preferred over using implicit defaults in the snap, because this way, users can easily discover which configuration options your snap supports.

On Ubuntu Core, a device’s `gadget snap </t/gadget-snaps/696>`__ can share default configuration options with the snaps listed in its ``gadget.yaml``. These options are shared when a snap is first installed using either the `default-configure hook </t/supported-snap-hooks/3795#heading--default-configure>`__, which is run before services are started, or with the `configure hook </t/supported-snap-hooks/3795#heading--the-configure-hook>`__, which runs after services are started.

The example implementation below includes managing a default value.


.. _heading--nested:

Nested values
-------------

You can group configuration options using a dotted path:

.. code:: bash

   snapctl set my-snap server.protocol=tcp server.port=4242

Each configuration option can be retrieved by using the same dotted path, or you can retrieve the entire collection as a json document by specifying their common key:

.. code:: bash

   $ snapctl get server
   {
       "protocol": "tcp",
       "port": "4242"
   }


.. _heading--example:

Implementation
--------------

A typical implementation will use the options set by the user to change environment variables within the snap environment which are then used by the snap application.

This kind of implementation can be split into 3 scripts:

-  **wrapper script** calls the application with the necessary environment variables
-  **management script** sets values, checks their validity, and restarts the application
-  **default-configure hook script** calls the management functions on first install before services are started
-  **configure hook script** calls the management functions on installation and changes

The above scripts will also need to be linked to a snap’s **snapcraft.yaml**.

When a user changes the configuration of a snap, the `configure hook script </t/supported-snap-hooks/3795#heading--the-configure-hook>`__ is always executed. Through functions in the management script, this hook will typically validate the configuration and, for example, update environment variables or write to the necessary configuration files.

   ⚠ Snaps that use configuration options need to have a ``configure`` hook defined. Otherwise, users will not be able to change the configuration.

The following example scripts show how to set and manage a port setting for a snap running an executable called ``example-server``.


.. _heading--management:

Example management script
^^^^^^^^^^^^^^^^^^^^^^^^^

A separate script for management functions allows those functions to be accessible from both the wrapper and the configure hook scripts.

In the following example, we simply define a default HTTP port and two functions:

-  ``http_port`` requests the default port if nothing is yet set and returns the port value
-  ``set_http_port``\ sets the port value

.. code:: bash

   #!/bin/sh

   DEFAULT_HTTP_PORT="80"

   http_port()
   {
           port="$(snapctl get ports.http)"
           if [ -z "$port" ]; then
                   port="$DEFAULT_HTTP_PORT"
                   set_http_port $port
           fi
           echo "$port"
   }

   set_http_port()
   {
           snapctl set ports.http="$1"
   }

The above script should be expanded to manage the running process and also to check whether the new port value is any different from the old, avoiding a potentially unnecessary service restart.


.. _heading--default-configure:

Example default-configure hook script
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The default-configure-hook is an optional extension to the `configure hook <heading--configure_>`__ (see below) that executes only on snap installation and before services are started.

The following example attempts to retrieve a default configuration option from a gadget and either writes this to a file, or writes a fallback value if the gadget option doesn’t exist:

.. code:: bash

   #!/bin/sh

   DEFAULT_GADGET_OPTION=”123”

   gadget_option="$(snapctl get gadget_option)"
   if [ -z "$gadget_option" ]; then
      gadget_option="$DEFAULT_GADGET_OPTION"
   fi

   mkdir -m 0600 $SNAP_DATA/options
   echo "option: $gadget_option" > $SNAP_DATA/options/gadget

The ``snapctl get|set|unset`` command, used in the management script works anywhere within the snap context: during execution of your applications and services, and in all the hooks of your snap.

However, when you change configuration during a hook, if the hook exits with a non-zero status code the configuration will *not* be applied. This is because the hook context is transactional - either every change is applied, or none are.


.. _heading--configure:

Example configure hook script
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The configure script is run by the snap daemon when a snap is installed and when any option is set or changed.

The below example checks the validity of the value set for the port and runs the *set_http_port* function before making sure any changes are reflected in the server by restarting it:

.. code:: bash

   #!/bin/sh

   # source the management script
   . "$SNAP/management-script"

   handle_port_config()
   {
           http_port="$(http_port)"

           # Validate HTTP port
           if ! expr "$http_port" : '^[0-9]\+$' > /dev/null; then
                   echo "\"$http_port\" is not a valid HTTP port" >&2
                   return 1
           fi

          # run function from management script
           set_http_port "$http_port"

           # Restart example-server to apply new config
           snapctl restart example-server
   }
   handle_port_config

The ``snapctl get|set|unset`` command used in the management script works anywhere within the snap context: during execution of your applications and services, and in all the hooks of your snap.

However, when you change configuration during a hook, if the hook exits with a non-zero status code the configuration will *not* be applied. This is because the hook context is transactional - either every change is applied, or none are.


.. _heading--wrapper:

Example wrapper script
^^^^^^^^^^^^^^^^^^^^^^

The wrapper script is used to retrieve whatever options have been set, and in our example, use these to set environment variables which can be used as arguments when running ``example-server``.

.. code:: bash

   #!/bin/sh
   # source the management script
   . "$SNAP/bin/management-script"

   # call the http_port function from the management script
   HTTP_PORT="$(http_port)"
   export HTTP_PORT

   "$SNAP/bin/example-server" -www "$HTTP_PORT"

Rather than using set options as environment variables for an executable, they could just as easily be written to a configuration file.

For more details on the environment variables accessible from within a snap, such as ``$SNAP`` used above, see `Environment variables </t/environment-variables/7983>`__.


.. _heading--snapcraft:

Example snapcraft.yaml
^^^^^^^^^^^^^^^^^^^^^^

To incorporate options, hooks and scripts into a pre-existing `snapcraft.yaml </t/the-snapcraft-format/8337>`__ the executable needs to be replaced with the wrapper script, and both the hook and management scripts need to be brought into the snap from external ``src/hooks/bin`` and ``src/utilities/bin`` directories respectively:

.. code:: yaml

   apps:
     example-server:
         command: bin/example-server-wrapper
         daemon: simple
         plugs: [..]
   [...]
     hooks:
         plugin: dump
         source: src/hooks/
         organize:
              bin/: snap/hooks/
   [...]
     scripts:
         plugin: dump
         source: src/utilities

With the above snap built and deployed, its port can be changed and retrieved with the following command:

.. code:: bash

   snap set example-server ports.http=8090

A setting can be verified with the *get* command:

::

   $ snap get domoticz-gm ports.http
   8090

For a complete options and configuration hook example, take a look at the `Nextcloud snap <https://github.com/nextcloud/nextcloud-snap>`__.
