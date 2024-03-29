.. raw:: html



``mx.symbol.khatri_rao``
================================================

Description
----------------------

Computes the Khatri-Rao product of the input matrices.

Given a collection of :math:`n` input matrices,

.. math::

   A_1 \in \mathbb{R}^{M_1 \times M}, \ldots, A_n \in \mathbb{R}^{M_n \times N},

the (column-wise) Khatri-Rao product is defined as the matrix,

.. math::

   X = A_1 \otimes \cdots \otimes A_n \in \mathbb{R}^{(M_1 \cdots M_n) \times N},

where the :math:`k` th column is equal to the column-wise outer product
:math:`{A_1}_k \otimes \cdots \otimes {A_n}_k` where :math:`{A_i}_k` is the kth
column of the ith matrix.

**Example**::
	 
	 >>> A = mx.nd.array([[1, -1],
	 >>>                  [2, -3]])
	 >>> B = mx.nd.array([[1, 4],
	 >>>                  [2, 5],
	 >>>                  [3, 6]])
	 >>> C = mx.nd.khatri_rao(A, B)
	 >>> print(C.asnumpy())
	 [[  1.  -4.]
	 [  2.  -5.]
	 [  3.  -6.]
	 [  2. -12.]
	 [  4. -15.]
	 [  6. -18.]]
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.khatri_rao(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``args``                               | NDArray-or-Symbol[].                                       |
|                                        |                                                            |
|                                        | Positional input matrices                                  |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/contrib/krprod.cc#L108


.. disqus::
   :disqus_identifier: mx.symbol.khatri_rao
