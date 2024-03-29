.. raw:: html



``mx.symbol.log2``
====================================

Description
----------------------

Returns element-wise Base-2 logarithmic value of the input.

``2**log2(x) = x``

The storage type of ``log2`` output is always dense




Usage
----------

.. code:: r

	mx.symbol.log2(...)

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


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_unary_op_basic.cc#L957


.. disqus::
   :disqus_identifier: mx.symbol.log2
