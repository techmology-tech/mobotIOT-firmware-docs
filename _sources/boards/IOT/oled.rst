OLED
====

IOT can expose an OLED display object at:

- ``mobotIOT.oled``

If OLED initialization fails, this object is ``None``.

What you can draw
-----------------

- ``display_text(text, x, y)``
- ``draw_line(x1, y1, x2, y2)``
- ``draw_rectangle(x, y, width, height, filled=False)``
- ``draw_circle(x0, y0, radius, filled=False)``
- ``draw_triangle(x0, y0, x1, y1, x2, y2, filled=False)``
- ``clear_screen()``

Quick test
----------

.. code-block:: python

   if mobotIOT.oled is None:
       print("OLED not available")
   else:
       mobotIOT.oled.clear_screen()
       mobotIOT.oled.display_text("Hello IOT", 0, 0)

Graphics example
----------------

.. code-block:: python

   if mobotIOT.oled:
       mobotIOT.oled.clear_screen()
       mobotIOT.oled.draw_rectangle(0, 0, 128, 64)
       mobotIOT.oled.draw_circle(64, 32, 12)
       mobotIOT.oled.draw_line(0, 63, 127, 0)
       mobotIOT.oled.display_text("OK", 54, 28)

.. tip::
   Use ``clear_screen()`` before drawing a new frame to avoid stale pixels.

.. warning::
   Guard all calls with ``if mobotIOT.oled is not None`` to avoid runtime errors.

Example
-------

.. tab-set::

   .. tab-item:: Text

      .. code-block:: python

         if mobotIOT.oled:
             mobotIOT.oled.clear_screen()
             mobotIOT.oled.display_text("Temp", 0, 0)
             mobotIOT.oled.display_text(25, 0, 10)

   .. tab-item:: Shapes

      .. code-block:: python

         if mobotIOT.oled:
             mobotIOT.oled.clear_screen()
             mobotIOT.oled.draw_triangle(10, 50, 60, 10, 110, 50)
             mobotIOT.oled.draw_rectangle(20, 20, 20, 15, filled=True)

Common mistakes
---------------

- Writing to OLED without checking availability.
- Drawing many objects without clearing when a fresh frame is intended.
- Using out-of-range coordinates and expecting clipping behavior.
