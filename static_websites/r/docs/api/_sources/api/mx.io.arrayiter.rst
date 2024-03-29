.. raw:: html



``mx.io.arrayiter``
======================================

Description
----------------------

Create MXDataIter compatible iterator from R's array

Usage
----------

.. code:: r

	mx.io.arrayiter(data, label, batch.size = 128, shuffle = FALSE)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | The data array.                                            |
+----------------------------------------+------------------------------------------------------------+
| ``label``                              | The label array.                                           |
+----------------------------------------+------------------------------------------------------------+
| ``batch.size``                         | The batch size used to pack the array.                     |
+----------------------------------------+------------------------------------------------------------+
| ``shuffle``                            | Whether shuffle the data                                   |
+----------------------------------------+------------------------------------------------------------+




.. disqus::
   :disqus_identifier: mx.io.arrayiter
