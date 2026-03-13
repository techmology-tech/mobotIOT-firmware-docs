Fan
===

The fan object is available at:

- ``mobotIOT.fan``

Main methods
------------

- ``on()`` / ``off()``
- ``set_speed(percent)``
- ``get_speed()``

``percent`` is clamped to ``0..100``.

Quick test
----------

.. code-block:: python

   mobotIOT.fan.set_speed(40)
   print("Fan speed:", mobotIOT.fan.get_speed())

Speed profile example
---------------------

.. code-block:: python

   import time

   for speed in [20, 40, 60, 80, 100, 0]:
       mobotIOT.fan.set_speed(speed)
       print("Fan speed:", mobotIOT.fan.get_speed(), "%")
       time.sleep(0.6)

Common mistakes
---------------

- Expecting values above ``100`` to increase speed beyond max.
- Forgetting to turn fan off at script end.
