.. raw:: html



``mx.symbol.random_poisson``
========================================================

Description
----------------------

Draw random samples from a Poisson distribution.

Samples are distributed according to a Poisson distribution parametrized by *lambda* (rate).
Samples will always be returned as a floating point data type.

**Example**::
	 
	 poisson(lam=4, shape=(2,2)) = [[ 5.,  2.],
	 [ 4.,  6.]]
	 

Usage
----------

.. code:: r

	mx.symbol.random_poisson(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``lam``                                | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Lambda parameter (rate) of the Poisson distribution.       |
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
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/random/sample_op.cc#L149


.. disqus::
   :disqus_identifier: mx.symbol.random_poisson
