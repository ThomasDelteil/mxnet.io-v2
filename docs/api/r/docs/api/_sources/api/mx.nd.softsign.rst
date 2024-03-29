.. raw:: html



``mx.nd.softsign``
====================================

Description
----------------------

Computes softsign of x element-wise.

.. math::

   y = x / (1 + abs(x))

The storage type of ``softsign`` output is always dense





Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The input array.                                           |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_unary_op_basic.cc#L145


.. disqus::
   :disqus_identifier: mx.nd.softsign
