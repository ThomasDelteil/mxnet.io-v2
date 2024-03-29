.. raw:: html



``mx.symbol.batch_take``
================================================

Description
----------------------

Takes elements from a data batch.

.. note::   `batch_take` is deprecated. Use `pick` instead.

Given an input array of shape ``(d0, d1)`` and indices of shape ``(i0,)``, the result will be
an output array of shape ``(i0,)`` with::

	 output[i] = input[i, indices[i]]
	 
**Example**::
	 
	 x = [[ 1.,  2.],
	 [ 3.,  4.],
	 [ 5.,  6.]]
	 
	 // takes elements with specified indices
	 batch_take(x, [0,1,0]) = [ 1.  4.  5.]
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.batch_take(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``a``                                  | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The input array                                            |
+----------------------------------------+------------------------------------------------------------+
| ``indices``                            | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The index array                                            |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/indexing_op.cc#L750


.. disqus::
   :disqus_identifier: mx.symbol.batch_take
