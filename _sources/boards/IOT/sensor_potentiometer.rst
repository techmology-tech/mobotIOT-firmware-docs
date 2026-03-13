Potentiometer
=============

The potentiometer object is available at:

- ``mobotIOT.pot``

What you can read
-----------------

- ``mobotIOT.pot.read()`` returns raw ADC value in ``0..4095``

Quick test
----------

.. code-block:: python

   print("Pot value:", mobotIOT.pot.read())

Mapping example
---------------

.. code-block:: python

   raw = mobotIOT.pot.read()
   percent = int(raw * 100 / 4095)
   print("Raw:", raw, "Percent:", percent)

Common mistakes
---------------

- Assuming values are linear under all hardware conditions.
- Forgetting to clamp mapped values in custom formulas.
