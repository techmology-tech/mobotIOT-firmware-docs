IOT Overview
============

Welcome to **IOT**.

At startup, your board gives you a ready-to-use ``mobotIOT`` object, so you can go
straight to sensing, display output, and actuator control.

What you can do quickly
-----------------------

- Read environment and input sensors
- Detect RFID cards
- Control LEDs, OLED graphics, and 7-segment output
- Drive actuator outputs (servo and fan)
- Play sound feedback with the buzzer

Explore by component
--------------------

.. toctree::
   :maxdepth: 1

   sensors
   rfid
   leds
   oled
   seven_segment
   actuators
   buzzer

Your first interaction script
-----------------------------

.. code-block:: python

   print("Temperature:", mobotIOT.dht11.read(0))
   print("Humidity:", mobotIOT.dht11.read(1))

   mobotIOT.led1.on()
   mobotIOT.rgb_led.write(0, 30, 0)
