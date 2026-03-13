LDR Sensor
==========

The light sensor object is available at:

- ``mobotIOT.ldr``

What you can read
-----------------

- ``mobotIOT.ldr.read()`` returns raw ADC value in ``0..4095``

Quick test
----------

.. code-block:: python

   print("Light level:", mobotIOT.ldr.read())

Monitoring example
------------------

.. code-block:: python

   import time

   while True:
       level = mobotIOT.ldr.read()
       print("LDR:", level)
       time.sleep(0.2)

Common mistakes
---------------

- Expecting lux units directly from raw ADC output.
- Comparing readings across setups without calibration.
