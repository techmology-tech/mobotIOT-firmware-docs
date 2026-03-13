Battery Sensor
==============

The battery sensor object is available at:

- ``mobotIOT.battery``

What you can read
-----------------

- ``mobotIOT.battery.read()`` returns battery voltage as rounded float (volts)

Quick test
----------

.. code-block:: python

   print("Battery:", mobotIOT.battery.read(), "V")

Monitoring example
------------------

.. code-block:: python

   import time

   for _ in range(20):
       v = mobotIOT.battery.read()
       print("Battery voltage:", v, "V")
       time.sleep(1)

Common mistakes
---------------

- Treating one reading as absolute battery health without trend checks.
- Comparing values across different load conditions without context.
