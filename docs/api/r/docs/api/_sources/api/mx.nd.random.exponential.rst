.. raw:: html



``mx.nd.random.exponential``
========================================================

Description
----------------------

Draw random samples from an exponential distribution.

Samples are distributed according to an exponential distribution parametrized by *lambda* (rate).

**Example**::
	 
	 exponential(lam=4, shape=(2,2)) = [[ 0.0097189 ,  0.08999364],
	 [ 0.04146638,  0.31715935]]
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``lam``                                | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Lambda parameter (rate) of the exponential distribution.   |
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


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/random/sample_op.cc#L136


.. disqus::
   :disqus_identifier: mx.nd.random.exponential
