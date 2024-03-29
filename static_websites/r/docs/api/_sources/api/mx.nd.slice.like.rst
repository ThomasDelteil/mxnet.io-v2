.. raw:: html



``mx.nd.slice.like``
========================================

Description
----------------------

Slices a region of the array like the shape of another array.

This function is similar to ``slice``, however, the `begin` are always `0`s
and `end` of specific axes are inferred from the second input `shape_like`.

Given the second `shape_like` input of ``shape=(d_0, d_1, ..., d_n-1)``,
a ``slice_like`` operator with default empty `axes`, it performs the
following operation:

`` out = slice(input, begin=(0, 0, ..., 0), end=(d_0, d_1, ..., d_n-1))``.

When `axes` is not empty, it is used to speficy which axes are being sliced.

Given a 4-d input data, ``slice_like`` operator with ``axes=(0, 2, -1)``
will perform the following operation:

`` out = slice(input, begin=(0, 0, 0, 0), end=(d_0, None, d_2, d_3))``.

Note that it is allowed to have first and second input with different dimensions,
however, you have to make sure the `axes` are specified and not exceeding the
dimension limits.

For example, given `input_1` with ``shape=(2,3,4,5)`` and `input_2` with
``shape=(1,2,3)``, it is not allowed to use:

`` out = slice_like(a, b)`` because ndim of `input_1` is 4, and ndim of `input_2`
is 3.

The following is allowed in this situation:

`` out = slice_like(a, b, axes=(0, 2))``

**Example**::
	 
	 x = [[  1.,   2.,   3.,   4.],
	 [  5.,   6.,   7.,   8.],
	 [  9.,  10.,  11.,  12.]]
	 
	 y = [[  0.,   0.,   0.],
	 [  0.,   0.,   0.]]
	 
	 slice_like(x, y) = [[ 1.,  2.,  3.]
	 [ 5.,  6.,  7.]]
	 slice_like(x, y, axes=(0, 1)) = [[ 1.,  2.,  3.]
	 [ 5.,  6.,  7.]]
	 slice_like(x, y, axes=(0)) = [[ 1.,  2.,  3.,  4.]
	 [ 5.,  6.,  7.,  8.]]
	 slice_like(x, y, axes=(-1)) = [[  1.,   2.,   3.]
	 [  5.,   6.,   7.]
	 [  9.,  10.,  11.]]
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Source input                                               |
+----------------------------------------+------------------------------------------------------------+
| ``shape.like``                         | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Shape like input                                           |
+----------------------------------------+------------------------------------------------------------+
| ``axes``                               | Shape(tuple), optional, default=[].                        |
|                                        |                                                            |
|                                        | List of axes on which input data will be sliced according  |
|                                        | to the corresponding size of the second input. By default  |
|                                        | will slice on all axes. Negative axes are                  |
|                                        | supported.                                                 |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/matrix_op.cc#L570


.. disqus::
   :disqus_identifier: mx.nd.slice.like
