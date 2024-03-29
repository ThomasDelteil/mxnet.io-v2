.. raw:: html



``mx.symbol.linalg_potrf``
====================================================

Description
----------------------

Performs Cholesky factorization of a symmetric positive-definite matrix.
Input is a tensor *A* of dimension *n >= 2*.

If *n=2*, the Cholesky factor *L* of the symmetric, positive definite matrix *A* is
computed. *L* is lower triangular (entries of upper triangle are all zero), has
positive diagonal entries, and:

*A* = *L* \* *L*\ :sup:`T`

If *n>2*, *potrf* is performed separately on the trailing two dimensions for all inputs
(batch mode).

.. note:: The operator supports float32 and float64 data types only.

**Example**::
	 
	 // Single matrix factorization
	 A = [[4.0, 1.0], [1.0, 4.25]]
	 potrf(A) = [[2.0, 0], [0.5, 2.0]]
	 
	 // Batch matrix factorization
	 A = [[[4.0, 1.0], [1.0, 4.25]], [[16.0, 4.0], [4.0, 17.0]]]
	 potrf(A) = [[[2.0, 0], [0.5, 2.0]], [[4.0, 0], [1.0, 4.0]]]
	 

Usage
----------

.. code:: r

	mx.symbol.linalg_potrf(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``A``                                  | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Tensor of input matrices to be decomposed                  |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/la_op.cc#L201


.. disqus::
   :disqus_identifier: mx.symbol.linalg_potrf
