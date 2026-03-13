LEDs
====

IOT provides light outputs through:

- ``mobotIOT.rgb_led``
- ``mobotIOT.led1``
- ``mobotIOT.led2``

What you can control
--------------------

**RGB LED**

- ``mobotIOT.rgb_led.write(r_percent, g_percent, b_percent)``
- each channel is clamped to ``0..100``

**Simple LEDs**

- ``on()`` / ``off()``
- ``toggle()``
- ``write_percent(percent)`` for PWM brightness on this board

Quick test
----------

.. code-block:: python

   mobotIOT.led1.on()
   mobotIOT.led2.off()
   mobotIOT.rgb_led.write(0, 50, 0)

Brightness and color example
----------------------------

.. code-block:: python

   import time

   mobotIOT.led1.write_percent(20)
   mobotIOT.led2.write_percent(80)

   mobotIOT.rgb_led.write(100, 0, 0)
   time.sleep(0.3)
   mobotIOT.rgb_led.write(0, 100, 0)
   time.sleep(0.3)
   mobotIOT.rgb_led.write(0, 0, 100)
   time.sleep(0.3)
   mobotIOT.rgb_led.write(0, 0, 0)

.. note::
   Percent values outside ``0..100`` are clamped automatically.

Example
-------

.. tab-set::

   .. tab-item:: Quick test

      .. code-block:: python

         mobotIOT.led1.toggle()
         mobotIOT.led2.toggle()

   .. tab-item:: Full script

      .. code-block:: python

         import time

         for _ in range(5):
             mobotIOT.led1.toggle()
             mobotIOT.led2.toggle()
             mobotIOT.rgb_led.write(0, 0, 25)
             time.sleep(0.2)
         mobotIOT.rgb_led.write(0, 0, 0)

Common mistakes
---------------

- Passing RGB values outside percent scale (use ``0..100``).
- Expecting ``toggle()`` on PWM LEDs to preserve intermediate brightness.
- Forgetting to turn RGB channels off after tests.
