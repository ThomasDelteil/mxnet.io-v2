.. raw:: html



``mx.nd.SwapAxis``
====================================

Description
----------------------

Interchanges two axes of an array.

**Example**::
	 
	 x = [[1, 2, 3]])
	 swapaxes(x, 0, 1) = [[ 1],
	 [ 2],
	 [ 3]]
	 
	 x = [[[ 0, 1],
	 [ 2, 3]],
	 [[ 4, 5],
	 [ 6, 7]]]  // (2,2,2) array
	 
	 swapaxes(x, 0, 2) = [[[ 0, 4],
	 [ 2, 6]],
	 [[ 1, 5],
	 [ 3, 7]]]
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input array.                                               |
+----------------------------------------+------------------------------------------------------------+
| ``dim1``                               | int (non-negative), optional, default=0.                   |
|                                        |                                                            |
|                                        | the first axis to be swapped.                              |
+----------------------------------------+------------------------------------------------------------+
| ``dim2``                               | int (non-negative), optional, default=0.                   |
|                                        |                                                            |
|                                        | the second axis to be swapped.                             |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/swapaxis.cc#L70


.. disqus::
   :disqus_identifier: mx.nd.SwapAxis
