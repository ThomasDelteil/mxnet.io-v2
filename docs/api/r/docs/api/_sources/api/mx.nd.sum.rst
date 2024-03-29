.. raw:: html



``mx.nd.sum``
==========================

Description
----------------------

Computes the sum of array elements over given axes.

.. Note::

	 `sum` and `sum_axis` are equivalent.
	 For ndarray of csr storage type summation along axis 0 and axis 1 is supported.
	 Setting keepdims or exclude to True will cause a fallback to dense operator.
	 
**Example**::
	 
	 data = [[[1, 2], [2, 3], [1, 3]],
	 [[1, 4], [4, 3], [5, 2]],
	 [[7, 1], [7, 2], [7, 3]]]
	 
	 sum(data, axis=1)
	 [[  4.   8.]
	 [ 10.   9.]
	 [ 21.   6.]]
	 
	 sum(data, axis=[1,2])
	 [ 12.  19.  27.]
	 
	 data = [[1, 2, 0],
	 [3, 0, 1],
	 [4, 1, 0]]
	 
	 csr = cast_storage(data, 'csr')
	 
	 sum(csr, axis=0)
	 [ 8.  3.  1.]
	 
	 sum(csr, axis=1)
	 [ 3.  4.  5.]
	 
	 
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The input                                                  |
+----------------------------------------+------------------------------------------------------------+
| ``axis``                               | Shape or None, optional, default=None.                     |
|                                        |                                                            |
|                                        | The axis or axes along which to perform the reduction.     |
|                                        |                                                            |
|                                        | The default, `axis=()`, will compute over all elements     |
|                                        | into                                                       |
|                                        | a                                                          |
|                                        | scalar array with shape `(1,)`.                            |
|                                        |                                                            |
|                                        | If `axis` is int, a reduction is performed on a particular |
|                                        | axis.                                                      |
|                                        |                                                            |
|                                        | If `axis` is a tuple of ints, a reduction is performed on  |
|                                        | all the                                                    |
|                                        | axes                                                       |
|                                        | specified in the tuple.                                    |
|                                        |                                                            |
|                                        | If `exclude` is true, reduction will be performed on the   |
|                                        | axes that                                                  |
|                                        | are                                                        |
|                                        | NOT in axis instead.                                       |
|                                        |                                                            |
|                                        | Negative values means indexing from right to left.         |
+----------------------------------------+------------------------------------------------------------+
| ``keepdims``                           | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | If this is set to `True`, the reduced axes are left in the |
|                                        | result as dimension with size                              |
|                                        | one.                                                       |
+----------------------------------------+------------------------------------------------------------+
| ``exclude``                            | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Whether to perform reduction on axis that are NOT in axis  |
|                                        | instead.                                                   |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/broadcast_reduce_op_value.cc#L116


.. disqus::
   :disqus_identifier: mx.nd.sum
