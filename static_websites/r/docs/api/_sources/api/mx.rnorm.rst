.. raw:: html



``mx.rnorm``
========================

Description
----------------------

Generate nomal distribution with mean and sd.

**Example**::

	 mx.set.seed(0)
	 as.array(mx.runif(2))
	 # 0.5488135 0.5928446
	 mx.set.seed(0)
	 as.array(mx.rnorm(2))
	 # 2.212206 1.163079
	 
	 
Usage
----------

.. code:: r

	mx.rnorm(shape, mean = 0, sd = 1, ctx = NULL)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``shape``                              | Dimension, The shape(dimension) of the result.             |
+----------------------------------------+------------------------------------------------------------+
| ``mean``                               | numeric, The mean of distribution.                         |
+----------------------------------------+------------------------------------------------------------+
| ``sd``                                 | numeric, The standard deviations.                          |
+----------------------------------------+------------------------------------------------------------+
| ``ctx``                                | optional The context device of the array. mx.ctx.default() |
|                                        | will be used in                                            |
|                                        | default.                                                   |
+----------------------------------------+------------------------------------------------------------+




.. disqus::
   :disqus_identifier: mx.rnorm
