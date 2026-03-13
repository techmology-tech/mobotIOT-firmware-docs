Servo
=====

The servo object is available at:

- ``mobotIOT.servo``

Main methods
------------

- ``set_angle(angle)``
- ``get_angle()``
- ``move_to(angle, step=5, delay_ms=20)``
- ``center()``, ``min()``, ``max()``
- ``sweep(start=0, end=180, step=5, delay_ms=20, cycles=1)``

Quick test
----------

.. code-block:: python

   mobotIOT.servo.center()
   mobotIOT.servo.set_angle(45)

Smooth movement example
-----------------------

.. code-block:: python

   import time

   mobotIOT.servo.move_to(150, step=3, delay_ms=15)
   time.sleep(0.4)
   mobotIOT.servo.move_to(30, step=3, delay_ms=15)
   time.sleep(0.4)
   mobotIOT.servo.center()

Sweep example
-------------

.. code-block:: python

   mobotIOT.servo.sweep(start=20, end=160, step=10, delay_ms=40, cycles=2)

.. warning::
   Angles are clamped to configured limits.

Common mistakes
---------------

- Using very large step values that cause abrupt movement.
- Ignoring mechanical limits of attached hardware.
