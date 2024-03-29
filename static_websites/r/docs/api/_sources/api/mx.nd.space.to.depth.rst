.. raw:: html



``mx.nd.space.to.depth``
================================================

Description
----------------------

Rearranges(permutes) blocks of spatial data into depth.
Similar to ONNX SpaceToDepth operator:
https://github.com/onnx/onnx/blob/master/docs/Operators.md#SpaceToDepth.  

The output is a new tensor where the values from height and width dimension are 
moved to the depth dimension. The reverse of this operation is ``depth_to_space``.

.. math::

	\begin{gather*}
    x \prime = reshape(x, [N, C, H / block\_size, block\_size, W / block\_size, block\_size]) \\
    x \prime \prime = transpose(x \prime, [0, 3, 5, 1, 2, 4]) \\
    y = reshape(x \prime \prime, [N, C * (block\_size ^ 2), H / block\_size, W / block\_size])
    \end{gather*}

where :math:`x` is an input tensor with default layout as :math:`[N, C, H, W]`: [batch, channels, height, width] 
and :math:`y` is the output tensor of layout :math:`[N, C * (block\_size ^ 2), H / block\_size, W / block\_size]`

**Example**::
	 
	 x = [[[[0, 6, 1, 7, 2, 8],
	 [12, 18, 13, 19, 14, 20],
	 [3, 9, 4, 10, 5, 11],
	 [15, 21, 16, 22, 17, 23]]]]
	 
	 
	 space_to_depth(x, 2) = [[[[0, 1, 2],
	 [3, 4, 5]],
	 [[6, 7, 8],
	 [9, 10, 11]],
	 [[12, 13, 14],
	 [15, 16, 17]],
	 [[18, 19, 20],
	 [21, 22, 23]]]]
	 


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

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/matrix_op.cc#L1000


.. disqus::
   :disqus_identifier: mx.nd.space.to.depth
