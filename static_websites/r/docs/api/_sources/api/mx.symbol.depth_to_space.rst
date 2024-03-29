.. raw:: html



``mx.symbol.depth_to_space``
========================================================

Description
----------------------

Rearranges(permutes) data from depth into blocks of spatial data.
Similar to ONNX DepthToSpace operator:
https://github.com/onnx/onnx/blob/master/docs/Operators.md#DepthToSpace.
The output is a new tensor where the values from depth dimension are moved in spatial blocks
to height and width dimension. The reverse of this operation is ``space_to_depth``.

.. math::

	\begin{gather*}
    x \prime = reshape(x, [N, block\_size, block\_size, C / (block\_size ^ 2), H * block\_size, W * block\_size]) \\
    x \prime \prime = transpose(x \prime, [0, 3, 4, 1, 5, 2]) \\
    y = reshape(x \prime \prime, [N, C / (block\_size ^ 2), H * block\_size, W * block\_size])
    \end{gather*}

where :math:`x` is an input tensor with default layout as :math:`[N, C, H, W]`: [batch, channels, height, width] 
and :math:`y` is the output tensor of layout :math:`[N, C / (block\_size ^ 2), H * block\_size, W * block\_size]`

**Example**::
	 
	 x = [[[[0, 1, 2],
	 [3, 4, 5]],
	 [[6, 7, 8],
	 [9, 10, 11]],
	 [[12, 13, 14],
	 [15, 16, 17]],
	 [[18, 19, 20],
	 [21, 22, 23]]]]
	 
	 depth_to_space(x, 2) = [[[[0, 6, 1, 7, 2, 8],
	 [12, 18, 13, 19, 14, 20],
	 [3, 9, 4, 10, 5, 11],
	 [15, 21, 16, 22, 17, 23]]]]
	 

Usage
----------

.. code:: r

	mx.symbol.depth_to_space(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input ndarray                                              |
+----------------------------------------+------------------------------------------------------------+
| ``block.size``                         | int, required.                                             |
|                                        |                                                            |
|                                        | Blocks of [block_size. block_size] are moved               |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/matrix_op.cc#L946


.. disqus::
   :disqus_identifier: mx.symbol.depth_to_space
