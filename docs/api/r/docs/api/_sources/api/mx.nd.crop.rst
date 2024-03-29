.. raw:: html



``mx.nd.crop``
============================

Description
----------------------

Slices a region of the array.

.. note:: ``crop`` is deprecated. Use ``slice`` instead.

This function returns a sliced array between the indices given
by `begin` and `end` with the corresponding `step`.

For an input array of ``shape=(d_0, d_1, ..., d_n-1)``,
slice operation with ``begin=(b_0, b_1...b_m-1)``,
``end=(e_0, e_1, ..., e_m-1)``, and ``step=(s_0, s_1, ..., s_m-1)``,
where m <= n, results in an array with the shape
``(|e_0-b_0|/|s_0|, ..., |e_m-1-b_m-1|/|s_m-1|, d_m, ..., d_n-1)``.

The resulting array's *k*-th dimension contains elements
from the *k*-th dimension of the input array starting
from index ``b_k`` (inclusive) with step ``s_k``
until reaching ``e_k`` (exclusive).

If the *k*-th elements are `None` in the sequence of `begin`, `end`,
and `step`, the following rule will be used to set default values.
If `s_k` is `None`, set `s_k=1`. If `s_k > 0`, set `b_k=0`, `e_k=d_k`;
else, set `b_k=d_k-1`, `e_k=-1`.

The storage type of ``slice`` output depends on storage types of inputs

- slice(csr) = csr
- otherwise, ``slice`` generates output with default storage

.. note:: When input data storage type is csr, it only supports step=(), or step=(None,), or step=(1,) to generate a csr output. For other step parameter values, it falls back to slicing a dense tensor.

**Example**::
	 
	 x = [[  1.,   2.,   3.,   4.],
	 [  5.,   6.,   7.,   8.],
	 [  9.,  10.,  11.,  12.]]
	 
	 slice(x, begin=(0,1), end=(2,4)) = [[ 2.,  3.,  4.],
	 [ 6.,  7.,  8.]]
	 slice(x, begin=(None, 0), end=(None, 3), step=(-1, 2)) = [[9., 11.],
	 [5.,  7.],
	 [1.,  3.]]
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Source input                                               |
+----------------------------------------+------------------------------------------------------------+
| ``begin``                              | Shape(tuple), required.                                    |
|                                        |                                                            |
|                                        | starting indices for the slice operation, supports         |
|                                        | negative                                                   |
|                                        | indices.                                                   |
+----------------------------------------+------------------------------------------------------------+
| ``end``                                | Shape(tuple), required.                                    |
|                                        |                                                            |
|                                        | ending indices for the slice operation, supports negative  |
|                                        | indices.                                                   |
+----------------------------------------+------------------------------------------------------------+
| ``step``                               | Shape(tuple), optional, default=[].                        |
|                                        |                                                            |
|                                        | step for the slice operation, supports negative values.    |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/matrix_op.cc#L414


.. disqus::
   :disqus_identifier: mx.nd.crop
