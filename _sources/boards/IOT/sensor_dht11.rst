DHT11 Sensor
============

The DHT11 object is available at:

- ``mobotIOT.dht11``

What you can read
-----------------

- ``mobotIOT.dht11.read(mode)``
- ``mode=0`` returns temperature (°C)
- ``mode=1`` returns humidity (%)
- any other value raises ``ValueError``

Quick test
----------

.. code-block:: python

   print("Temperature:", mobotIOT.dht11.read(0), "C")
   print("Humidity:", mobotIOT.dht11.read(1), "%")

Monitoring example
------------------

.. code-block:: python

   import time

   for _ in range(10):
       t = mobotIOT.dht11.read(0)
       h = mobotIOT.dht11.read(1)
       print("T/H:", t, h)
       time.sleep(1)

.. warning::
   ``read(mode)`` only accepts ``0`` or ``1``.

Common mistakes
---------------

- Calling ``read(2)`` or any unsupported mode.
- Reading too aggressively in very tight loops without delays.
