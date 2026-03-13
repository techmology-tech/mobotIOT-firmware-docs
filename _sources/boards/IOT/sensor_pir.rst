PIR Sensor
==========

The PIR motion sensor object is available at:

- ``mobotIOT.pir``

What you can read
-----------------

- ``mobotIOT.pir.motion_detected()`` returns ``True`` when motion is detected

Quick test
----------

.. code-block:: python

   print("Motion:", mobotIOT.pir.motion_detected())

Monitoring example
------------------

.. code-block:: python

   import time

   while True:
       if mobotIOT.pir.motion_detected():
           print("Motion detected")
       else:
           print("No motion")
       time.sleep(0.3)

Common mistakes
---------------

- Expecting stable output without short sampling delay.
- Treating the return value as numeric levels instead of boolean state.
