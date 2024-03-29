.. raw:: html



``mx.nd.broadcast.logical.or``
============================================================

Description
----------------------

Returns the result of element-wise **logical or** with broadcasting.

**Example**::
	 
	 x = [[ 1.,  1.,  0.],
	 [ 1.,  1.,  0.]]
	 
	 y = [[ 1.],
	 [ 0.]]
	 
	 broadcast_logical_or(x, y) = [[ 1.,  1.,  1.],
	 [ 1.,  1.,  0.]]
	 
	 
	 


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

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_binary_broadcast_op_logic.cc#L172


.. disqus::
   :disqus_identifier: mx.nd.broadcast.logical.or
