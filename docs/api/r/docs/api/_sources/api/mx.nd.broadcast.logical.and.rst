.. raw:: html



``mx.nd.broadcast.logical.and``
==============================================================

Description
----------------------

Returns the result of element-wise **logical and** with broadcasting.

**Example**::
	 
	 x = [[ 1.,  1.,  1.],
	 [ 1.,  1.,  1.]]
	 
	 y = [[ 0.],
	 [ 1.]]
	 
	 broadcast_logical_and(x, y) = [[ 0.,  0.,  0.],
	 [ 1.,  1.,  1.]]
	 
	 
	 


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


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_binary_broadcast_op_logic.cc#L154


.. disqus::
   :disqus_identifier: mx.nd.broadcast.logical.and
