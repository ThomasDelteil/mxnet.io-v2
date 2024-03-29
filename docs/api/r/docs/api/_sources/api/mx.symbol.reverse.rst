.. raw:: html



``mx.symbol.reverse``
==========================================

Description
----------------------

Reverses the order of elements along given axis while preserving array shape.

Note: reverse and flip are equivalent. We use reverse in the following examples.

**Example**::
	 
	 x = [[ 0.,  1.,  2.,  3.,  4.],
	 [ 5.,  6.,  7.,  8.,  9.]]
	 
	 reverse(x, axis=0) = [[ 5.,  6.,  7.,  8.,  9.],
	 [ 0.,  1.,  2.,  3.,  4.]]
	 
	 reverse(x, axis=1) = [[ 4.,  3.,  2.,  1.,  0.],
	 [ 9.,  8.,  7.,  6.,  5.]]
	 

Usage
----------

.. code:: r

	mx.symbol.reverse(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input data array                                           |
+----------------------------------------+------------------------------------------------------------+
| ``axis``                               | Shape(tuple), required.                                    |
|                                        |                                                            |
|                                        | The axis which to reverse elements.                        |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/matrix_op.cc#L794


.. disqus::
   :disqus_identifier: mx.symbol.reverse
