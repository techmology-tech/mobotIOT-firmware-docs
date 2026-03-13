RFID
====

IOT can expose an RFID reader object at:

- ``mobotIOT.rfid``

If RFID initialization fails, this object is ``None``.

What you can do
---------------

- ``mobotIOT.rfid.is_card_present()`` checks if any card is detected
- ``mobotIOT.rfid.read()`` returns UID as lowercase hex string, or ``None``

Quick test
----------

.. code-block:: python

   if mobotIOT.rfid is None:
       print("RFID not available")
   else:
       print("RFID ready")

Read card UID example
---------------------

.. code-block:: python

   import time

   if mobotIOT.rfid is None:
       print("RFID not available")
   else:
       print("Bring a card close to the reader...")
       for _ in range(40):
           uid = mobotIOT.rfid.read()
           if uid is not None:
               print("Card UID:", uid)
               break
           time.sleep(0.1)

.. tip::
   Check ``is_card_present()`` before ``read()`` when you need to avoid repeated full reads.

.. warning::
   Always guard RFID access with ``if mobotIOT.rfid is not None``.

Example
-------

.. tab-set::

   .. tab-item:: Presence only

      .. code-block:: python

         if mobotIOT.rfid and mobotIOT.rfid.is_card_present():
             print("Card detected")

   .. tab-item:: UID polling loop

      .. code-block:: python

         import time

         while True:
             if mobotIOT.rfid is None:
                 print("RFID not available")
                 break
             uid = mobotIOT.rfid.read()
             if uid:
                 print("UID:", uid)
             time.sleep(0.2)

Common mistakes
---------------

- Calling ``mobotIOT.rfid.read()`` without checking for ``None`` first.
- Expecting every poll to return a UID (no card returns ``None``).
- Treating UID format as decimal instead of lowercase hexadecimal text.
