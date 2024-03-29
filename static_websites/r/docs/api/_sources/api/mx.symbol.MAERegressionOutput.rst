.. raw:: html



``mx.symbol.MAERegressionOutput``
==================================================================

Description
----------------------

Computes mean absolute error of the input.

MAE is a risk metric corresponding to the expected value of the absolute error.

If :math:`\hat{y}_i` is the predicted value of the i-th sample, and :math:`y_i` is the corresponding target value,
then the mean absolute error (MAE) estimated over :math:`n` samples is defined as

:math:`\text{MAE}(\textbf{Y}, \hat{\textbf{Y}} ) = \frac{1}{n} \sum_{i=0}^{n-1} \lVert \textbf{y}_i - \hat{\textbf{y}}_i \rVert_1`

.. note::    Use the MAERegressionOutput as the final output layer of a net.

The storage type of ``label`` can be ``default`` or ``csr``

- MAERegressionOutput(default, default) = default
- MAERegressionOutput(default, csr) = default

By default, gradients of this loss function are scaled by factor `1/m`, where m is the number of regression outputs of a training example.
The parameter `grad_scale` can be used to change this scale to `grad_scale/m`.




Usage
----------

.. code:: r

	mx.symbol.MAERegressionOutput(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input data to the function.                                |
+----------------------------------------+------------------------------------------------------------+
| ``label``                              | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input label to the function.                               |
+----------------------------------------+------------------------------------------------------------+
| ``grad.scale``                         | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Scale the gradient by a float factor                       |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/regression_output.cc#L120


.. disqus::
   :disqus_identifier: mx.symbol.MAERegressionOutput
