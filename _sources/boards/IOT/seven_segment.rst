7-Segment Display
=================

IOT uses a TM1637-based 3-digit display.

Initialization flow
-------------------

- Call ``mobotIOT.init_seg()`` to initialize the display
- Access the display object through ``mobotIOT.seg``
- If initialization fails, ``mobotIOT.seg`` remains ``None``

What you can display
--------------------

- ``mobotIOT.seg.show(value)`` for short text/numeric display
- ``mobotIOT.seg.number(n)`` for integer display
- ``mobotIOT.seg.float(value)`` for compact float display
- ``mobotIOT.seg.set_segments_for_digit(digit, segments_list)`` for segment-level control

Quick test
----------

.. code-block:: python

   mobotIOT.init_seg()
   if mobotIOT.seg is None:
       print("7-segment not available")
   else:
       mobotIOT.seg.show("123")

Counter example
---------------

.. code-block:: python

   import time

   mobotIOT.init_seg()
   if mobotIOT.seg:
       for i in range(0, 100):
           mobotIOT.seg.number(i)
           time.sleep(0.05)

Segment-level example
---------------------

.. code-block:: python

   mobotIOT.init_seg()
   if mobotIOT.seg:
       mobotIOT.seg.set_segments_for_digit(0, ["A", "B", "C", "D", "E", "F"])
       mobotIOT.seg.set_segments_for_digit(1, ["A", "D", "G"])
       mobotIOT.seg.set_segments_for_digit(2, ["A", "B", "G", "E", "D", "DP"])

.. note::
   ``float(value)`` may simplify precision to fit the available 3 digits.

Common mistakes
---------------

- Forgetting to call ``mobotIOT.init_seg()`` before using ``mobotIOT.seg``.
- Assuming ``mobotIOT.seg`` is always available after startup.
- Passing invalid digit index to ``set_segments_for_digit``.
