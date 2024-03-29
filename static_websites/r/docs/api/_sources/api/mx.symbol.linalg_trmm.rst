.. raw:: html



``mx.symbol.linalg_trmm``
==================================================

Description
----------------------

Performs multiplication with a lower triangular matrix.
Input are tensors *A*, *B*, each of dimension *n >= 2* and having the same shape
on the leading *n-2* dimensions.

If *n=2*, *A* must be lower triangular. The operator performs the BLAS3 function
*trmm*:

*out* = *alpha* \* *op*\ (*A*) \* *B*

if *rightside=False*, or

*out* = *alpha* \* *B* \* *op*\ (*A*)

if *rightside=True*. Here, *alpha* is a scalar parameter, and *op()* is either the
identity or the matrix transposition (depending on *transpose*).

If *n>2*, *trmm* is performed separately on the trailing two dimensions for all inputs
(batch mode).

.. note:: The operator supports float32 and float64 data types only.

**Example**::
	 
	 // Single triangular matrix multiply
	 A = [[1.0, 0], [1.0, 1.0]]
	 B = [[1.0, 1.0, 1.0], [1.0, 1.0, 1.0]]
	 trmm(A, B, alpha=2.0) = [[2.0, 2.0, 2.0], [4.0, 4.0, 4.0]]
	 
	 // Batch triangular matrix multiply
	 A = [[[1.0, 0], [1.0, 1.0]], [[1.0, 0], [1.0, 1.0]]]
	 B = [[[1.0, 1.0, 1.0], [1.0, 1.0, 1.0]], [[0.5, 0.5, 0.5], [0.5, 0.5, 0.5]]]
	 trmm(A, B, alpha=2.0) = [[[2.0, 2.0, 2.0], [4.0, 4.0, 4.0]],
	 [[1.0, 1.0, 1.0], [2.0, 2.0, 2.0]]]
	 

Usage
----------

.. code:: r

	mx.symbol.linalg_trmm(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``A``                                  | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Tensor of lower triangular matrices                        |
+----------------------------------------+------------------------------------------------------------+
| ``B``                                  | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Tensor of matrices                                         |
+----------------------------------------+------------------------------------------------------------+
| ``transpose``                          | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Use transposed of the triangular matrix                    |
+----------------------------------------+------------------------------------------------------------+
| ``rightside``                          | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Multiply triangular matrix from the right to               |
|                                        | non-triangular                                             |
|                                        | one.                                                       |
+----------------------------------------+------------------------------------------------------------+
| ``alpha``                              | double, optional, default=1.                               |
|                                        |                                                            |
|                                        | Scalar factor to be applied to the result.                 |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/la_op.cc#L316


.. disqus::
   :disqus_identifier: mx.symbol.linalg_trmm
