.. raw:: html



``mx.nd.make.loss``
======================================

Description
----------------------

Make your own loss function in network construction.

This operator accepts a customized loss function symbol as a terminal loss and
the symbol should be an operator with no backward dependency.
The output of this function is the gradient of loss with respect to the input data.

For example, if you are a making a cross entropy loss function. Assume ``out`` is the
predicted output and ``label`` is the true label, then the cross entropy can be defined as::

	 cross_entropy = label * log(out) + (1 - label) * log(1 - out)
	 loss = make_loss(cross_entropy)
	 
	 We will need to use ``make_loss`` when we are creating our own loss function or we want to
	 combine multiple loss functions. Also we may want to stop some variables' gradients
	 from backpropagation. See more detail in ``BlockGrad`` or ``stop_gradient``.
	 
	 The storage type of ``make_loss`` output depends upon the input storage type:
	 
	- make_loss(default) = default
	- make_loss(row_sparse) = row_sparse
	 
	 
	 


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


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/elemwise_unary_op_basic.cc#L300


.. disqus::
   :disqus_identifier: mx.nd.make.loss
