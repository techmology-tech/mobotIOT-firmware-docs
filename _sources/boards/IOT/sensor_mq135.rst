MQ135 Sensor
============

The MQ135 gas sensor object is available at:

- ``mobotIOT.mq135``

What you can read
-----------------

- ``mobotIOT.mq135.read()`` returns raw ADC value in ``0..4095``

Quick test
----------

.. code-block:: python

   print("MQ135:", mobotIOT.mq135.read())

Monitoring example
------------------

.. code-block:: python

   import time

   for _ in range(20):
       value = mobotIOT.mq135.read()
       print("Gas level:", value)
       time.sleep(0.2)

.. tip::
   Use moving averages if you need smoother dashboards.

Common mistakes
---------------

- Assuming returned values are already calibrated gas concentration.
- Ignoring normal ADC noise when comparing single samples.
