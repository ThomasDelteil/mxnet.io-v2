.. raw:: html



``mx.symbol.sample_gamma``
====================================================

Description
----------------------

Concurrent sampling from multiple
gamma distributions with parameters *alpha* (shape) and *beta* (scale).

The parameters of the distributions are provided as input arrays.
Let *[s]* be the shape of the input arrays, *n* be the dimension of *[s]*, *[t]*
be the shape specified as the parameter of the operator, and *m* be the dimension
of *[t]*. Then the output will be a *(n+m)*-dimensional array with shape *[s]x[t]*.

For any valid *n*-dimensional index *i* with respect to the input arrays, *output[i]*
will be an *m*-dimensional array that holds randomly drawn samples from the distribution
which is parameterized by the input values at index *i*. If the shape parameter of the
operator is not set, then one sample will be drawn per distribution and the output array
has the same shape as the input arrays.

**Example**::
	 
	 alpha = [ 0.0, 2.5 ]
	 beta = [ 1.0, 0.7 ]
	 
	 // Draw a single sample for each distribution
	 sample_gamma(alpha, beta) = [ 0.        ,  2.25797319]
	 
	 // Draw a vector containing two samples for each distribution
	 sample_gamma(alpha, beta, shape=(2)) = [[ 0.        ,  0.        ],
	 [ 2.25797319,  1.70734084]]
	 

Usage
----------

.. code:: r

	mx.symbol.sample_gamma(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``alpha``                              | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Alpha (shape) parameters of the distributions.             |
+----------------------------------------+------------------------------------------------------------+
| ``shape``                              | Shape(tuple), optional, default=[].                        |
|                                        |                                                            |
|                                        | Shape to be sampled from each random distribution.         |
+----------------------------------------+------------------------------------------------------------+
| ``dtype``                              | {'None', 'float16', 'float32', 'float64'},optional,        |
|                                        | default='None'.                                            |
|                                        |                                                            |
|                                        | DType of the output in case this can't be inferred.        |
|                                        | Defaults to float32 if not defined                         |
|                                        | (dtype=None).                                              |
+----------------------------------------+------------------------------------------------------------+
| ``beta``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Beta (scale) parameters of the distributions.              |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/random/multisample_op.cc#L282


.. disqus::
   :disqus_identifier: mx.symbol.sample_gamma
