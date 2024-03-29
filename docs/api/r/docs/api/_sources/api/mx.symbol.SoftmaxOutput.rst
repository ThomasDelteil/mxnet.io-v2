.. raw:: html



``mx.symbol.SoftmaxOutput``
======================================================

Description
----------------------

Computes the gradient of cross entropy loss with respect to softmax output.

- This operator computes the gradient in two steps.
  The cross entropy loss does not actually need to be computed.

- Applies softmax function on the input array.
  - Computes and returns the gradient of cross entropy loss w.r.t. the softmax output.

- The softmax function, cross entropy loss and gradient is given by:

- Softmax Function:

.. math:: \text{softmax}(x)_i = \frac{exp(x_i)}{\sum_j exp(x_j)}

	- Cross Entropy Function:

.. math:: \text{CE(label, output)} = - \sum_i \text{label}_i \log(\text{output}_i)

	- The gradient of cross entropy loss w.r.t softmax output:

.. math:: \text{gradient} = \text{output} - \text{label}

	- During forward propagation, the softmax function is computed for each instance in the input array.

For general *N*-D input arrays with shape :math:`(d_1, d_2, ..., d_n)`. The size is
  :math:`s=d_1 \cdot d_2 \cdot \cdot \cdot d_n`. We can use the parameters `preserve_shape`
  and `multi_output` to specify the way to compute softmax:

- By default, `preserve_shape` is ``false``. This operator will reshape the input array
    into a 2-D array with shape :math:`(d_1, \frac{s}{d_1})` and then compute the softmax function for
    each row in the reshaped array, and afterwards reshape it back to the original shape
    :math:`(d_1, d_2, ..., d_n)`.
  - If `preserve_shape` is ``true``, the softmax function will be computed along
    the last axis (`axis` = ``-1``).
  - If `multi_output` is ``true``, the softmax function will be computed along
    the second axis (`axis` = ``1``).

- During backward propagation, the gradient of cross-entropy loss w.r.t softmax output array is computed.
  The provided label can be a one-hot label array or a probability label array.

- If the parameter `use_ignore` is ``true``, `ignore_label` can specify input instances
    with a particular label to be ignored during backward propagation. **This has no effect when
    softmax `output` has same shape as `label`**.

**Example**::
	 
	 data = [[1,2,3,4],[2,2,2,2],[3,3,3,3],[4,4,4,4]]
	 label = [1,0,2,3]
	 ignore_label = 1
	 SoftmaxOutput(data=data, label = label,\
	 multi_output=true, use_ignore=true,\
	 ignore_label=ignore_label)
	 ## forward softmax output
	 [[ 0.0320586   0.08714432  0.23688284  0.64391428]
	 [ 0.25        0.25        0.25        0.25      ]
	 [ 0.25        0.25        0.25        0.25      ]
	 [ 0.25        0.25        0.25        0.25      ]]
	 ## backward gradient output
	 [[ 0.    0.    0.    0.  ]
	 [-0.75  0.25  0.25  0.25]
	 [ 0.25  0.25 -0.75  0.25]
	 [ 0.25  0.25  0.25 -0.75]]
	 ## notice that the first row is all 0 because label[0] is 1, which is equal to ignore_label.
	 
	 - The parameter `grad_scale` can be used to rescale the gradient, which is often used to
	 give each loss function different weights.
	 
	 - This operator also supports various ways to normalize the gradient by `normalization`,
	 The `normalization` is applied if softmax output has different shape than the labels.
	 The `normalization` mode can be set to the followings:
	 
	- ``'null'``: do nothing.
	- ``'batch'``: divide the gradient by the batch size.
	- ``'valid'``: divide the gradient by the number of instances which are not ignored.
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.SoftmaxOutput(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input array.                                               |
+----------------------------------------+------------------------------------------------------------+
| ``label``                              | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Ground truth label.                                        |
+----------------------------------------+------------------------------------------------------------+
| ``grad.scale``                         | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Scales the gradient by a float factor.                     |
+----------------------------------------+------------------------------------------------------------+
| ``ignore.label``                       | float, optional, default=-1.                               |
|                                        |                                                            |
|                                        | The instances whose `labels` == `ignore_label` will be     |
|                                        | ignored during backward, if `use_ignore` is set to         |
|                                        | ``true``).                                                 |
+----------------------------------------+------------------------------------------------------------+
| ``multi.output``                       | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | If set to ``true``, the softmax function will be computed  |
|                                        | along axis ``1``. This is applied when the shape of input  |
|                                        | array differs from the shape of label                      |
|                                        | array.                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``use.ignore``                         | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | If set to ``true``, the `ignore_label` value will not      |
|                                        | contribute to the backward                                 |
|                                        | gradient.                                                  |
+----------------------------------------+------------------------------------------------------------+
| ``preserve.shape``                     | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | If set to ``true``, the softmax function will be computed  |
|                                        | along the last axis                                        |
|                                        | (``-1``).                                                  |
+----------------------------------------+------------------------------------------------------------+
| ``normalization``                      | {'batch', 'null', 'valid'},optional, default='null'.       |
|                                        |                                                            |
|                                        | Normalizes the gradient.                                   |
+----------------------------------------+------------------------------------------------------------+
| ``out.grad``                           | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Multiplies gradient with output gradient element-wise.     |
+----------------------------------------+------------------------------------------------------------+
| ``smooth.alpha``                       | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | Constant for computing a label smoothed version of         |
|                                        | cross-entropyfor the backwards pass. This constant gets    |
|                                        | subtracted from theone-hot encoding of the gold label and  |
|                                        | distributed uniformly toall other                          |
|                                        | labels.                                                    |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/softmax_output.cc#L123


.. disqus::
   :disqus_identifier: mx.symbol.SoftmaxOutput
