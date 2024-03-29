.. raw:: html



``mx.nd.topk``
============================

Description
----------------------

Returns the top *k* elements in an input array along the given axis.
The returned elements will be sorted.

**Example**::
	 
	 x = [[ 0.3,  0.2,  0.4],
	 [ 0.1,  0.3,  0.2]]
	 
	 // returns an index of the largest element on last axis
	 topk(x) = [[ 2.],
	 [ 1.]]
	 
	 // returns the value of top-2 largest elements on last axis
	 topk(x, ret_typ='value', k=2) = [[ 0.4,  0.3],
	 [ 0.3,  0.2]]
	 
	 // returns the value of top-2 smallest elements on last axis
	 topk(x, ret_typ='value', k=2, is_ascend=1) = [[ 0.2 ,  0.3],
	 [ 0.1 ,  0.2]]
	 
	 // returns the value of top-2 largest elements on axis 0
	 topk(x, axis=0, ret_typ='value', k=2) = [[ 0.3,  0.3,  0.4],
	 [ 0.1,  0.2,  0.2]]
	 
	 // flattens and then returns list of both values and indices
	 topk(x, ret_typ='both', k=2) = [[[ 0.4,  0.3], [ 0.3,  0.2]] ,  [[ 2.,  0.], [ 1.,  2.]]]
	 
	 
	 


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
|                                        | Axis along which to choose the top k indices. If not       |
|                                        | given, the flattened array is used. Default is             |
|                                        | -1.                                                        |
+----------------------------------------+------------------------------------------------------------+
| ``k``                                  | int, optional, default='1'.                                |
|                                        |                                                            |
|                                        | Number of top elements to select, should be always smaller |
|                                        | than or equal to the element number in the given axis. A   |
|                                        | global sort is performed if set k <                        |
|                                        | 1.                                                         |
+----------------------------------------+------------------------------------------------------------+
| ``ret.typ``                            | {'both', 'indices', 'mask', 'value'},optional,             |
|                                        | default='indices'.                                         |
|                                        |                                                            |
|                                        | The return type.                                           |
|                                        | "value" means to return the top k values, "indices" means  |
|                                        | to return the indices of the top k values, "mask" means to |
|                                        | return a mask array containing 0 and 1. 1 means the top k  |
|                                        | values. "both" means to return a list of both values and   |
|                                        | indices of top k                                           |
|                                        | elements.                                                  |
+----------------------------------------+------------------------------------------------------------+
| ``is.ascend``                          | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Whether to choose k largest or k smallest elements. Top K  |
|                                        | largest elements will be chosen if set to                  |
|                                        | false.                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``dtype``                              | {'float16', 'float32', 'float64', 'int32',                 |
|                                        | 'uint8'},optional,                                         |
|                                        | default='float32'.                                         |
|                                        |                                                            |
|                                        | DType of the output indices when ret_typ is "indices" or   |
|                                        | "both". An error will be raised if the selected data type  |
|                                        | cannot precisely represent the                             |
|                                        | indices.                                                   |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/ordering_op.cc#L64


.. disqus::
   :disqus_identifier: mx.nd.topk
