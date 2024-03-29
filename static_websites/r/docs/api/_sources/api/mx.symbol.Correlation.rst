.. raw:: html



``mx.symbol.Correlation``
==================================================

Description
----------------------

Applies correlation to inputs.

The correlation layer performs multiplicative patch comparisons between two feature maps.

Given two multi-channel feature maps :math:`f_{1}, f_{2}`, with :math:`w`, :math:`h`, and :math:`c` being their width, height, and number of channels,
the correlation layer lets the network compare each patch from :math:`f_{1}` with each patch from :math:`f_{2}`.

For now we consider only a single comparison of two patches. The 'correlation' of two patches centered at :math:`x_{1}` in the first map and
:math:`x_{2}` in the second map is then defined as:

.. math::

	c(x_{1}, x_{2}) = \sum_{o \in [-k,k] \times [-k,k]} <f_{1}(x_{1} + o), f_{2}(x_{2} + o)>

for a square patch of size :math:`K:=2k+1`.

Note that the equation above is identical to one step of a convolution in neural networks, but instead of convolving data with a filter, it convolves data with other
data. For this reason, it has no training weights.

Computing :math:`c(x_{1}, x_{2})` involves :math:`c * K^{2}` multiplications. Comparing all patch combinations involves :math:`w^{2}*h^{2}` such computations.

Given a maximum displacement :math:`d`, for each location :math:`x_{1}` it computes correlations :math:`c(x_{1}, x_{2})` only in a neighborhood of size :math:`D:=2d+1`,
by limiting the range of :math:`x_{2}`. We use strides :math:`s_{1}, s_{2}`, to quantize :math:`x_{1}` globally and to quantize :math:`x_{2}` within the neighborhood
centered around :math:`x_{1}`.

The final output is defined by the following expression:

.. math::

  out[n, q, i, j] = c(x_{i, j}, x_{q})

where :math:`i` and :math:`j` enumerate spatial locations in :math:`f_{1}`, and :math:`q` denotes the :math:`q^{th}` neighborhood of :math:`x_{i,j}`.


Usage
----------

.. code:: r

	mx.symbol.Correlation(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data1``                              | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input data1 to the correlation.                            |
+----------------------------------------+------------------------------------------------------------+
| ``data2``                              | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input data2 to the correlation.                            |
+----------------------------------------+------------------------------------------------------------+
| ``kernel.size``                        | int (non-negative), optional, default=1.                   |
|                                        |                                                            |
|                                        | kernel size for Correlation must be an odd number          |
+----------------------------------------+------------------------------------------------------------+
| ``max.displacement``                   | int (non-negative), optional, default=1.                   |
|                                        |                                                            |
|                                        | Max displacement of Correlation                            |
+----------------------------------------+------------------------------------------------------------+
| ``stride1``                            | int (non-negative), optional, default=1.                   |
|                                        |                                                            |
|                                        | stride1 quantize data1 globally                            |
+----------------------------------------+------------------------------------------------------------+
| ``stride2``                            | int (non-negative), optional, default=1.                   |
|                                        |                                                            |
|                                        | stride2 quantize data2 within the neighborhood centered    |
|                                        | around                                                     |
|                                        | data1                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``pad.size``                           | int (non-negative), optional, default=0.                   |
|                                        |                                                            |
|                                        | pad for Correlation                                        |
+----------------------------------------+------------------------------------------------------------+
| ``is.multiply``                        | boolean, optional, default=1.                              |
|                                        |                                                            |
|                                        | operation type is either multiplication or subduction      |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/correlation.cc#L198


.. disqus::
   :disqus_identifier: mx.symbol.Correlation
