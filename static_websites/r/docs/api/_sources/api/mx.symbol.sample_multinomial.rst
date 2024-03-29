.. raw:: html



``mx.symbol.sample_multinomial``
================================================================

Description
----------------------

Concurrent sampling from multiple multinomial distributions.

*data* is an *n* dimensional array whose last dimension has length *k*, where
*k* is the number of possible outcomes of each multinomial distribution. This
operator will draw *shape* samples from each distribution. If shape is empty
one sample will be drawn from each distribution.

If *get_prob* is true, a second array containing log likelihood of the drawn
samples will also be returned. This is usually used for reinforcement learning
where you can provide reward as head gradient for this array to estimate
gradient.

Note that the input distribution must be normalized, i.e. *data* must sum to
1 along its last axis.

**Example**::
	 
	 probs = [[0, 0.1, 0.2, 0.3, 0.4], [0.4, 0.3, 0.2, 0.1, 0]]
	 
	 // Draw a single sample for each distribution
	 sample_multinomial(probs) = [3, 0]
	 
	 // Draw a vector containing two samples for each distribution
	 sample_multinomial(probs, shape=(2)) = [[4, 2],
	 [0, 0]]
	 
	 // requests log likelihood
	 sample_multinomial(probs, get_prob=True) = [2, 1], [0.2, 0.3]
	 
Usage
----------

.. code:: r

	mx.symbol.sample_multinomial(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Distribution probabilities. Must sum to one on the last    |
|                                        | axis.                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``shape``                              | Shape(tuple), optional, default=[].                        |
|                                        |                                                            |
|                                        | Shape to be sampled from each random distribution.         |
+----------------------------------------+------------------------------------------------------------+
| ``get.prob``                           | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Whether to also return the log probability of sampled      |
|                                        | result. This is usually used for differentiating through   |
|                                        | stochastic variables, e.g. in reinforcement                |
|                                        | learning.                                                  |
+----------------------------------------+------------------------------------------------------------+
| ``dtype``                              | {'float16', 'float32', 'float64', 'int32',                 |
|                                        | 'uint8'},optional,                                         |
|                                        | default='int32'.                                           |
|                                        |                                                            |
|                                        | DType of the output in case this can't be inferred.        |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol



.. disqus::
   :disqus_identifier: mx.symbol.sample_multinomial
