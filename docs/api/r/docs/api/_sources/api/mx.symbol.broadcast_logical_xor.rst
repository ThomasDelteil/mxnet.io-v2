.. raw:: html



``mx.symbol.broadcast_logical_xor``
======================================================================

Description
----------------------

Returns the result of element-wise **logical xor** with broadcasting.

**Example**::
	 
	 x = [[ 1.,  1.,  0.],
	 [ 1.,  1.,  0.]]
	 
	 y = [[ 1.],
	 [ 0.]]
	 
	 broadcast_logical_xor(x, y) = [[ 0.,  0.,  1.],
	 [ 1.,  1.,  0.]]
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.broadcast_logical_xor(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``lhs``                                | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | First input to the function                                |
+----------------------------------------+------------------------------------------------------------+
| ``rhs``                                | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Second input to the function                               |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_binary_broadcast_op_logic.cc#L190


.. disqus::
   :disqus_identifier: mx.symbol.broadcast_logical_xor
