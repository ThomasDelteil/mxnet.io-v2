.. raw:: html



``mx.symbol.ones_like``
==============================================

Description
----------------------

Return an array of ones with the same shape and type
as the input array.

**Example**::
	 
	 x = [[ 0.,  0.,  0.],
	 [ 0.,  0.,  0.]]
	 
	 ones_like(x) = [[ 1.,  1.,  1.],
	 [ 1.,  1.,  1.]]
	 
Usage
----------

.. code:: r

	mx.symbol.ones_like(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The input                                                  |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol



.. disqus::
   :disqus_identifier: mx.symbol.ones_like
