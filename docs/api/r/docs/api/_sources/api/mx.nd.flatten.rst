.. raw:: html



``mx.nd.flatten``
==================================

Description
----------------------

Flattens the input array into a 2-D array by collapsing the higher dimensions.

.. note:: `Flatten` is deprecated. Use `flatten` instead.

For an input array with shape ``(d1, d2, ..., dk)``, `flatten` operation reshapes
the input array into an output array of shape ``(d1, d2*...*dk)``.

Note that the bahavior of this function is different from numpy.ndarray.flatten,
which behaves similar to mxnet.ndarray.reshape((-1,)).

**Example**::
	 
	 x = [[
	 [1,2,3],
	 [4,5,6],
	 [7,8,9]
	 ],
	 [    [1,2,3],
	 [4,5,6],
	 [7,8,9]
	 ]],
	 
	 flatten(x) = [[ 1.,  2.,  3.,  4.,  5.,  6.,  7.,  8.,  9.],
	 [ 1.,  2.,  3.,  4.,  5.,  6.,  7.,  8.,  9.]]
	 
	 
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input array.                                               |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/matrix_op.cc#L259


.. disqus::
   :disqus_identifier: mx.nd.flatten
