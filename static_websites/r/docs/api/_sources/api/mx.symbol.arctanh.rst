.. raw:: html



``mx.symbol.arctanh``
==========================================

Description
----------------------

Returns the element-wise inverse hyperbolic tangent of the input array, \
computed element-wise.

The storage type of ``arctanh`` output depends upon the input storage type:

	- arctanh(default) = default
	- arctanh(row_sparse) = row_sparse
	- arctanh(csr) = csr




Usage
----------

.. code:: r

	mx.symbol.arctanh(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The input array.                                           |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_unary_op_trig.cc#L281


.. disqus::
   :disqus_identifier: mx.symbol.arctanh
