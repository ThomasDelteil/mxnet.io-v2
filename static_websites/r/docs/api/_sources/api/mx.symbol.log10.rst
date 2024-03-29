.. raw:: html



``mx.symbol.log10``
======================================

Description
----------------------

Returns element-wise Base-10 logarithmic value of the input.

``10**log10(x) = x``

The storage type of ``log10`` output is always dense




Usage
----------

.. code:: r

	mx.symbol.log10(...)

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


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_unary_op_basic.cc#L945


.. disqus::
   :disqus_identifier: mx.symbol.log10
