Button
======

The button object is available at:

- ``mobotIOT.button``

What you can read
-----------------

- ``mobotIOT.button.is_pressed(debounce_ms=50)``
- returns ``True`` when button is pressed

Quick test
----------

.. code-block:: python

   print("Pressed:", mobotIOT.button.is_pressed())

Polling example
---------------

.. code-block:: python

   import time

   while True:
       if mobotIOT.button.is_pressed(50):
           print("Button pressed")
       time.sleep(0.05)

.. tip::
   Increase ``debounce_ms`` in electrically noisy conditions.

Common mistakes
---------------

- Using too small debounce value and getting false triggers.
- Polling in a tight loop with no delay.
