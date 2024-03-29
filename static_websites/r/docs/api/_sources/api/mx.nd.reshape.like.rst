.. raw:: html



``mx.nd.reshape.like``
============================================

Description
----------------------

Reshape some or all dimensions of `lhs` to have the same shape as some or all dimensions of `rhs`.

Returns a **view** of the `lhs` array with a new shape without altering any data.

**Example**::
	 
	 x = [1, 2, 3, 4, 5, 6]
	 y = [[0, -4], [3, 2], [2, 2]]
	 reshape_like(x, y) = [[1, 2], [3, 4], [5, 6]]
	 
	 More precise control over how dimensions are inherited is achieved by specifying \
	 slices over the `lhs` and `rhs` array dimensions. Only the sliced `lhs` dimensions \
	 are reshaped to the `rhs` sliced dimensions, with the non-sliced `lhs` dimensions staying the same.
	 
	 **Example**::
	 
	 - lhs shape = (30,7), rhs shape = (15,2,4), lhs_begin=0, lhs_end=1, rhs_begin=0, rhs_end=2, output shape = (15,2,7)
	 - lhs shape = (3, 5), rhs shape = (1,15,4), lhs_begin=0, lhs_end=2, rhs_begin=1, rhs_end=2, output shape = (15)
	 
	 Negative indices are supported, and `None` can be used for either `lhs_end` or `rhs_end` to indicate the end of the range.
	 
**Example**::
	 
	 - lhs shape = (30, 12), rhs shape = (4, 2, 2, 3), lhs_begin=-1, lhs_end=None, rhs_begin=1, rhs_end=None, output shape = (30, 2, 2, 3)
	 
	 
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``lhs``                                | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | First input.                                               |
+----------------------------------------+------------------------------------------------------------+
| ``rhs``                                | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Second input.                                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_unary_op_basic.cc#L455


.. disqus::
   :disqus_identifier: mx.nd.reshape.like
