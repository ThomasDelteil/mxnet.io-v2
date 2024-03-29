.. raw:: html



``mx.nd.LinearRegressionOutput``
================================================================

Description
----------------------

Computes and optimizes for squared loss during backward propagation.
Just outputs ``data`` during forward propagation.

If :math:`\hat{y}_i` is the predicted value of the i-th sample, and :math:`y_i` is the corresponding target value,
then the squared loss estimated over :math:`n` samples is defined as

:math:`\text{SquaredLoss}(\textbf{Y}, \hat{\textbf{Y}} ) = \frac{1}{n} \sum_{i=0}^{n-1} \lVert  \textbf{y}_i - \hat{\textbf{y}}_i  \rVert_2`

.. note::    Use the LinearRegressionOutput as the final output layer of a net.

The storage type of ``label`` can be ``default`` or ``csr``

- LinearRegressionOutput(default, default) = default
- LinearRegressionOutput(default, csr) = default

By default, gradients of this loss function are scaled by factor `1/m`, where m is the number of regression outputs of a training example.
The parameter `grad_scale` can be used to change this scale to `grad_scale/m`.





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

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/regression_output.cc#L92


.. disqus::
   :disqus_identifier: mx.nd.LinearRegressionOutput
