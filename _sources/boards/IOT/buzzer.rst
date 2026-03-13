Buzzer
======

IOT exposes a buzzer object at:

- ``mobotIOT.buzzer``

What you can play
-----------------

- ``play_sound(frequency, duration_ms)`` (blocking)
- ``play_note(note, duration_ms)`` (blocking)
- ``play_sequence(sequence)`` (non-blocking)
- ``stop()``
- ``is_busy()``

Built-in musical notes are available through note names such as ``"C4"``, ``"E5"``, ``"A4"``.

Quick test
----------

.. code-block:: python

   mobotIOT.buzzer.play_note("C5", 120)

Non-blocking sequence example
-----------------------------

.. code-block:: python

   import time

   seq = [("C4", 120), ("E4", 120), ("G4", 120), ("C5", 250)]
   mobotIOT.buzzer.play_sequence(seq)

   while mobotIOT.buzzer.is_busy():
       print("Playing...")
       time.sleep(0.1)

Play by frequency example
-------------------------

.. code-block:: python

   # 440 Hz = A4
   mobotIOT.buzzer.play_sound(440, 200)

.. note::
   ``play_sequence`` is non-blocking and runs in the background using a timer.

.. warning::
   Starting a new sequence automatically stops the currently running sequence.

Example
-------

.. tab-set::

   .. tab-item:: Quick test

      .. code-block:: python

         mobotIOT.buzzer.play_sound(880, 100)

   .. tab-item:: Full script

      .. code-block:: python

         import time

         melody = [("E5", 100), ("G5", 100), ("E5", 100), ("C5", 180)]
         mobotIOT.buzzer.play_sequence(melody)

         while mobotIOT.buzzer.is_busy():
             time.sleep(0.05)

         mobotIOT.buzzer.play_note("C4", 200)

Common mistakes
---------------

- Expecting ``play_sequence`` to block code execution.
- Using invalid note names (unknown names play silence for that note duration).
- Forgetting to call ``stop()`` when aborting an active sequence.
