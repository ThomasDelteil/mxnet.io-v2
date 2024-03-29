.. raw:: html



``mx.symbol.broadcast_mul``
======================================================

Description
----------------------

Returns element-wise product of the input arrays with broadcasting.

**Example**::
	 
	 x = [[ 1.,  1.,  1.],
	 [ 1.,  1.,  1.]]
	 
	 y = [[ 0.],
	 [ 1.]]
	 
	 broadcast_mul(x, y) = [[ 0.,  0.,  0.],
	 [ 1.,  1.,  1.]]
	 
	 Supported sparse operations:
	 
	 broadcast_mul(csr, dense(1D)) = csr
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.broadcast_mul(...)

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


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_binary_broadcast_op_basic.cc#L146


.. disqus::
   :disqus_identifier: mx.symbol.broadcast_mul
