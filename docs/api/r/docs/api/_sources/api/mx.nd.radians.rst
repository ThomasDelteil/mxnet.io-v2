.. raw:: html



``mx.nd.radians``
==================================

Description
----------------------

Converts each element of the input array from degrees to radians.

.. math::

   radians([0, 90, 180, 270, 360]) = [0, \pi/2, \pi, 3\pi/2, 2\pi]

The storage type of ``radians`` output depends upon the input storage type:

	- radians(default) = default
	- radians(row_sparse) = row_sparse
	- radians(csr) = csr





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


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_unary_op_trig.cc#L182


.. disqus::
   :disqus_identifier: mx.nd.radians
