.. raw:: html



``mx.symbol.logical_not``
==================================================

Description
----------------------

Returns the result of logical NOT (!) function.  

Example:
  logical_not([-2., 0., 1.]) = [0., 1., 0.]

Usage
----------

.. code:: r

	mx.symbol.logical_not(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The input array.                                           |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol



.. disqus::
   :disqus_identifier: mx.symbol.logical_not
