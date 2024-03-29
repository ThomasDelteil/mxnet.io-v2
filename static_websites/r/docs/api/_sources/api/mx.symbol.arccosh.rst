.. raw:: html



``mx.symbol.arccosh``
==========================================

Description
----------------------

Returns the element-wise inverse hyperbolic cosine of the input array, \
computed element-wise.

The storage type of ``arccosh`` output is always dense


Usage
----------

.. code:: r

	mx.symbol.arccosh(...)

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


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_unary_op_trig.cc#L264


.. disqus::
   :disqus_identifier: mx.symbol.arccosh
