.. 13090.md

.. \_the-audio-record-interface:

The audio-record interface
==========================

The ``audio-record`` interface allows an application to access your audio recording hardware, such as a microphone, via your system’s audio service, such as PulseAudio. It’s disabled by default.

This interface is a companion interface to the `audio-playback <the-audio-playback-interface.md>`__ interface, and is not intended to be used without it.

.. raw:: html

   <h2 id="the-audio-record-interface-heading--example">

Example

.. raw:: html

   </h2>

The brilliant `OBS Studio <https://snapcraft.io/obs-studio>`__ is a good example of an application that needs access to your microphone/audio recording hardware.

.. code:: bash

   $ sudo snap connect obs-studio:audio-record

[note type=“positive” status=“Interface documentation”]

See `Interface management <interface-management.md>`__ and `Supported interfaces <supported-interfaces.md>`__ for further details on how interfaces are used. [/note]

--------------

.. raw:: html

   <h2 id="the-audio-record-interface-heading--dev-details">

Developer details

.. raw:: html

   </h2>

**Auto-connect**: no

The design of this interface is based on the principle that the slot implementation of the audio service, such as `PulseAudio <the-pulseaudio-interface.md>`__, queries whether its audio-record slot is connected, leaving the audio service to mediate recording if it is.

On systems with snapd integration, PulseAudio’s mediation is limited and will only verify that the *snap* is connected to ``audio-record`` and not if the specific snap command plugs the interface.

.. raw:: html

   <h3 id="the-audio-record-interface-heading-code">

Code examples

.. raw:: html

   </h3>

Mumble is a voice chat platform and a good example of an application using audio-record. Its snapcraft.yaml can be found here: `https://github.com/snapcrafters/mumble/blob/master/snap/snapcraft.yaml <https://github.com/snapcrafters/mumble/blob/b5f1644a72a14cacd17b862cd0265d21d8ce604a/snap/snapcraft.yaml#L21>`__

The source code for this interface is in the *snapd* repository: https://github.com/snapcore/snapd/blob/master/interfaces/builtin/audio_record.go
