.. raw:: html



``mx.symbol.broadcast_minus``
==========================================================

Description
----------------------

Returns element-wise difference of the input arrays with broadcasting.

`broadcast_minus` is an alias to the function `broadcast_sub`.

**Example**::
	 
	 x = [[ 1.,  1.,  1.],
	 [ 1.,  1.,  1.]]
	 
	 y = [[ 0.],
	 [ 1.]]
	 
	 broadcast_sub(x, y) = [[ 1.,  1.,  1.],
	 [ 0.,  0.,  0.]]
	 
	 broadcast_minus(x, y) = [[ 1.,  1.,  1.],
	 [ 0.,  0.,  0.]]
	 
	 Supported sparse operations:
	 
	 broadcast_sub/minus(csr, dense(1D)) = dense
	 broadcast_sub/minus(dense(1D), csr) = dense
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.broadcast_minus(...)

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


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_binary_broadcast_op_basic.cc#L106


.. disqus::
   :disqus_identifier: mx.symbol.broadcast_minus
