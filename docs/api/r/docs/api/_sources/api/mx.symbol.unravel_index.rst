.. raw:: html



``mx.symbol.unravel_index``
======================================================

Description
----------------------

Converts an array of flat indices into a batch of index arrays. The operator follows numpy conventions so a single multi index is given by a column of the output matrix.

**Example**::
	 
	 A = [22,41,37]
	 unravel(A, shape=(7,6)) = [[3,6,6],[4,5,1]]
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.unravel_index(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Array of flat indices                                      |
+----------------------------------------+------------------------------------------------------------+
| ``shape``                              | Shape(tuple), optional, default=[].                        |
|                                        |                                                            |
|                                        | Shape of the array into which the multi-indices apply.     |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/ravel.cc#L65


.. disqus::
   :disqus_identifier: mx.symbol.unravel_index
