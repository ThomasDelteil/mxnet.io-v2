.. raw:: html



``mx.nd.BatchNorm``
======================================

Description
----------------------

Batch normalization.

Normalizes a data batch by mean and variance, and applies a scale ``gamma`` as
well as offset ``beta``.

Assume the input has more than one dimension and we normalize along axis 1.
We first compute the mean and variance along this axis:

.. math::

	data\_mean[i] = mean(data[:,i,:,...]) \\
  data\_var[i] = var(data[:,i,:,...])

Then compute the normalized output, which has the same shape as input, as following:

.. math::

	out[:,i,:,...] = \frac{data[:,i,:,...] - data\_mean[i]}{\sqrt{data\_var[i]+\epsilon}} * gamma[i] + beta[i]

Both *mean* and *var* returns a scalar by treating the input as a vector.

Assume the input has size *k* on axis 1, then both ``gamma`` and ``beta``
have shape *(k,)*. If ``output_mean_var`` is set to be true, then outputs both ``data_mean`` and
the inverse of ``data_var``, which are needed for the backward pass. Note that gradient of these
two outputs are blocked.

Besides the inputs and the outputs, this operator accepts two auxiliary
states, ``moving_mean`` and ``moving_var``, which are *k*-length
vectors. They are global statistics for the whole dataset, which are updated
by::

	 moving_mean = moving_mean * momentum + data_mean * (1 - momentum)
	 moving_var = moving_var * momentum + data_var * (1 - momentum)
	 
	 If ``use_global_stats`` is set to be true, then ``moving_mean`` and
	 ``moving_var`` are used instead of ``data_mean`` and ``data_var`` to compute
	 the output. It is often used during inference.
	 
	 The parameter ``axis`` specifies which axis of the input shape denotes
	 the 'channel' (separately normalized groups).  The default is 1.  Specifying -1 sets the channel
	 axis to be the last item in the input shape.
	 
	 Both ``gamma`` and ``beta`` are learnable parameters. But if ``fix_gamma`` is true,
	 then set ``gamma`` to 1 and its gradient to 0.
	 
Note::

	 When fix_gamma is set to True, no sparse support is provided. If fix_gamma is set to False,
	 the sparse tensors will fallback.
	 
	 
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input data to batch normalization                          |
+----------------------------------------+------------------------------------------------------------+
| ``gamma``                              | NDArray-or-Symbol                                          |
|                                        | gamma array                                                |
+----------------------------------------+------------------------------------------------------------+
| ``beta``                               | NDArray-or-Symbol                                          |
|                                        | beta array                                                 |
+----------------------------------------+------------------------------------------------------------+
| ``moving.mean``                        | NDArray-or-Symbol                                          |
|                                        | running mean of input                                      |
+----------------------------------------+------------------------------------------------------------+
| ``moving.var``                         | NDArray-or-Symbol                                          |
|                                        | running variance of input                                  |
+----------------------------------------+------------------------------------------------------------+
| ``eps``                                | double, optional, default=0.001.                           |
|                                        |                                                            |
|                                        | Epsilon to prevent div 0. Must be no less than             |
|                                        | CUDNN_BN_MIN_EPSILON defined in cudnn.h when using cudnn   |
|                                        | (usually                                                   |
|                                        | 1e-5)                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``momentum``                           | float, optional, default=0.9.                              |
|                                        |                                                            |
|                                        | Momentum for moving average                                |
+----------------------------------------+------------------------------------------------------------+
| ``fix.gamma``                          | boolean, optional, default=1.                              |
|                                        |                                                            |
|                                        | Fix gamma while training                                   |
+----------------------------------------+------------------------------------------------------------+
| ``use.global.stats``                   | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Whether use global moving statistics instead of local      |
|                                        | batch-norm. This will force change batch-norm into a scale |
|                                        | shift                                                      |
|                                        | operator.                                                  |
+----------------------------------------+------------------------------------------------------------+
| ``output.mean.var``                    | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Output the mean and inverse std                            |
+----------------------------------------+------------------------------------------------------------+
| ``axis``                               | int, optional, default='1'.                                |
|                                        |                                                            |
|                                        | Specify which shape axis the channel is specified          |
+----------------------------------------+------------------------------------------------------------+
| ``cudnn.off``                          | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Do not select CUDNN operator, if available                 |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/nn/batch_norm.cc#L575


.. disqus::
   :disqus_identifier: mx.nd.BatchNorm
