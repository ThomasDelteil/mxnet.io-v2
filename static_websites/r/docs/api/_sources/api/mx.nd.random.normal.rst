.. raw:: html



``mx.nd.random.normal``
==============================================

Description
----------------------

Draw random samples from a normal (Gaussian) distribution.

.. note:: The existing alias ``normal`` is deprecated.

Samples are distributed according to a normal distribution parametrized by *loc* (mean) and *scale*
(standard deviation).

**Example**::
	 
	 normal(loc=0, scale=1, shape=(2,2)) = [[ 1.89171135, -1.16881478],
	 [-1.23474145,  1.55807114]]
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``loc``                                | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | Mean of the distribution.                                  |
+----------------------------------------+------------------------------------------------------------+
| ``scale``                              | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Standard deviation of the distribution.                    |
+----------------------------------------+------------------------------------------------------------+
| ``shape``                              | Shape(tuple), optional, default=[].                        |
|                                        |                                                            |
|                                        | Shape of the output.                                       |
+----------------------------------------+------------------------------------------------------------+
| ``ctx``                                | string, optional, default=''.                              |
|                                        |                                                            |
|                                        | Context of output, in format [cpu|gpu|cpu_pinned](n). Only |
|                                        | used for imperative                                        |
|                                        | calls.                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``dtype``                              | {'None', 'float16', 'float32', 'float64'},optional,        |
|                                        | default='None'.                                            |
|                                        |                                                            |
|                                        | DType of the output in case this can't be inferred.        |
|                                        | Defaults to float32 if not defined                         |
|                                        | (dtype=None).                                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/random/sample_op.cc#L112


.. disqus::
   :disqus_identifier: mx.nd.random.normal
