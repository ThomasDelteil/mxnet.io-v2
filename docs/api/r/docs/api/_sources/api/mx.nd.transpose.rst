.. raw:: html



``mx.nd.transpose``
======================================

Description
----------------------

Permutes the dimensions of an array.

**Example**::
	 
	 x = [[ 1, 2],
	 [ 3, 4]]
	 
	 transpose(x) = [[ 1.,  3.],
	 [ 2.,  4.]]
	 
	 x = [[[ 1.,  2.],
	 [ 3.,  4.]],
	 
	 [[ 5.,  6.],
	 [ 7.,  8.]]]
	 
	 transpose(x) = [[[ 1.,  5.],
	 [ 3.,  7.]],
	 
	 [[ 2.,  6.],
	 [ 4.,  8.]]]
	 
	 transpose(x, axes=(1,0,2)) = [[[ 1.,  2.],
	 [ 5.,  6.]],
	 
	 [[ 3.,  4.],
	 [ 7.,  8.]]]
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Source input                                               |
+----------------------------------------+------------------------------------------------------------+
| ``axes``                               | Shape(tuple), optional, default=[].                        |
|                                        |                                                            |
|                                        | Target axis order. By default the axes will be inverted.   |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/matrix_op.cc#L312


.. disqus::
   :disqus_identifier: mx.nd.transpose
