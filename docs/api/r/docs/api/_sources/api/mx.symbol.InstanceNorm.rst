.. raw:: html



``mx.symbol.InstanceNorm``
====================================================

Description
----------------------

Applies instance normalization to the n-dimensional input array.

This operator takes an n-dimensional input array where (n>2) and normalizes
the input using the following formula:

.. math::

	out = \frac{x - mean[data]}{ \sqrt{Var[data]} + \epsilon} * gamma + beta

This layer is similar to batch normalization layer (`BatchNorm`)
with two differences: first, the normalization is
carried out per example (instance), not over a batch. Second, the
same normalization is applied both at test and train time. This
operation is also known as `contrast normalization`.

If the input data is of shape [batch, channel, spacial_dim1, spacial_dim2, ...],
`gamma` and `beta` parameters must be vectors of shape [channel].

This implementation is based on paper:

.. [1] Instance Normalization: The Missing Ingredient for Fast Stylization,
   D. Ulyanov, A. Vedaldi, V. Lempitsky, 2016 (arXiv:1607.08022v2).

**Example**::
	 
	 // Input of shape (2,1,2)
	 x = [[[ 1.1,  2.2]],
	 [[ 3.3,  4.4]]]
	 
	 // gamma parameter of length 1
	 gamma = [1.5]
	 
	 // beta parameter of length 1
	 beta = [0.5]
	 
	 // Instance normalization is calculated with the above formula
	 InstanceNorm(x,gamma,beta) = [[[-0.997527  ,  1.99752665]],
	 [[-0.99752653,  1.99752724]]]
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.InstanceNorm(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | An n-dimensional input array (n > 2) of the form [batch,   |
|                                        | channel, spatial_dim1, spatial_dim2,                       |
|                                        | ...].                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``gamma``                              | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | A vector of length 'channel', which multiplies the         |
|                                        | normalized                                                 |
|                                        | input.                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``beta``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | A vector of length 'channel', which is added to the        |
|                                        | product of the normalized input and the                    |
|                                        | weight.                                                    |
+----------------------------------------+------------------------------------------------------------+
| ``eps``                                | float, optional, default=0.001.                            |
|                                        |                                                            |
|                                        | An `epsilon` parameter to prevent division by 0.           |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/instance_norm.cc#L95


.. disqus::
   :disqus_identifier: mx.symbol.InstanceNorm
