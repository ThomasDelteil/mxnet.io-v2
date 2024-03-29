.. raw:: html



``mx.symbol.hard_sigmoid``
====================================================

Description
----------------------

Computes hard sigmoid of x element-wise.

.. math::

   y = max(0, min(1, alpha * x + beta))


Usage
----------

.. code:: r

	mx.symbol.hard_sigmoid(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The input array.                                           |
+----------------------------------------+------------------------------------------------------------+
| ``alpha``                              | float, optional, default=0.2.                              |
|                                        |                                                            |
|                                        | Slope of hard sigmoid                                      |
+----------------------------------------+------------------------------------------------------------+
| ``beta``                               | float, optional, default=0.5.                              |
|                                        |                                                            |
|                                        | Bias of hard sigmoid.                                      |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_unary_op_basic.cc#L115


.. disqus::
   :disqus_identifier: mx.symbol.hard_sigmoid
