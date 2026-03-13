mobotIOT User Guide
===================

Welcome! This guide is written for learners, students, and makers using the mobotIOT
board with MicroPython.

If you just got your board, start with the IOT board pages below. Each page has:

- A simple overview
- Clear component-by-component pages
- Ready-to-run code snippets

.. toctree::
   :maxdepth: 2
   :caption: Boards

   boards/index

First control example
---------------------

.. code-block:: python

   print("Temperature:", mobotIOT.dht11.read(0))
   mobotIOT.led1.on()
   mobotIOT.rgb_led.write(0, 30, 0)
