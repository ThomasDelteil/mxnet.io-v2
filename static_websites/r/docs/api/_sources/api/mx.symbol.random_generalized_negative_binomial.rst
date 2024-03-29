.. raw:: html



``mx.symbol.random_generalized_negative_binomial``
====================================================================================================

Description
----------------------

Draw random samples from a generalized negative binomial distribution.

Samples are distributed according to a generalized negative binomial distribution parametrized by
*mu* (mean) and *alpha* (dispersion). *alpha* is defined as *1/k* where *k* is the failure limit of the
number of unsuccessful experiments (generalized to real numbers).
Samples will always be returned as a floating point data type.

**Example**::
	 
	 generalized_negative_binomial(mu=2.0, alpha=0.3, shape=(2,2)) = [[ 2.,  1.],
	 [ 6.,  4.]]
	 

Usage
----------

.. code:: r

	mx.symbol.random_generalized_negative_binomial(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``mu``                                 | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Mean of the negative binomial distribution.                |
+----------------------------------------+------------------------------------------------------------+
| ``alpha``                              | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Alpha (dispersion) parameter of the negative binomial      |
|                                        | distribution.                                              |
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


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/random/sample_op.cc#L178


.. disqus::
   :disqus_identifier: mx.symbol.random_generalized_negative_binomial
