.. raw:: html



``mx.symbol.uniform``
==========================================

Description
----------------------

Draw random samples from a uniform distribution.

.. note:: The existing alias ``uniform`` is deprecated.

Samples are uniformly distributed over the half-open interval *[low, high)*
(includes *low*, but excludes *high*).

**Example**::
	 
	 uniform(low=0, high=1, shape=(2,2)) = [[ 0.60276335,  0.85794562],
	 [ 0.54488319,  0.84725171]]
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.uniform(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``low``                                | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | Lower bound of the distribution.                           |
+----------------------------------------+------------------------------------------------------------+
| ``high``                               | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Upper bound of the distribution.                           |
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


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/random/sample_op.cc#L95


.. disqus::
   :disqus_identifier: mx.symbol.uniform
