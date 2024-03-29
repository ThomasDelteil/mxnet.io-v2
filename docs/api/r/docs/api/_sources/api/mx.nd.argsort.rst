.. raw:: html



``mx.nd.argsort``
==================================

Description
----------------------

Returns the indices that would sort an input array along the given axis.

This function performs sorting along the given axis and returns an array of indices having same shape
as an input array that index data in sorted order.

**Example**::
	 
	 x = [[ 0.3,  0.2,  0.4],
	 [ 0.1,  0.3,  0.2]]
	 
	 // sort along axis -1
	 argsort(x) = [[ 1.,  0.,  2.],
	 [ 0.,  2.,  1.]]
	 
	 // sort along axis 0
	 argsort(x, axis=0) = [[ 1.,  0.,  1.]
	 [ 0.,  1.,  0.]]
	 
	 // flatten and then sort
	 argsort(x) = [ 3.,  1.,  5.,  0.,  4.,  2.]
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The input array                                            |
+----------------------------------------+------------------------------------------------------------+
| ``axis``                               | int or None, optional, default='-1'.                       |
|                                        |                                                            |
|                                        | Axis along which to sort the input tensor. If not given,   |
|                                        | the flattened array is used. Default is                    |
|                                        | -1.                                                        |
+----------------------------------------+------------------------------------------------------------+
| ``is.ascend``                          | boolean, optional, default=1.                              |
|                                        |                                                            |
|                                        | Whether to sort in ascending or descending order.          |
+----------------------------------------+------------------------------------------------------------+
| ``dtype``                              | {'float16', 'float32', 'float64', 'int32',                 |
|                                        | 'uint8'},optional,                                         |
|                                        | default='float32'.                                         |
|                                        |                                                            |
|                                        | DType of the output indices. It is only valid when ret_typ |
|                                        | is "indices" or "both". An error will be raised if the     |
|                                        | selected data type cannot precisely represent the          |
|                                        | indices.                                                   |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/ordering_op.cc#L177


.. disqus::
   :disqus_identifier: mx.nd.argsort
