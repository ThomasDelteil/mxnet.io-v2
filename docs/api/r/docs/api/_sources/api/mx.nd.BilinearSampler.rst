.. raw:: html



``mx.nd.BilinearSampler``
==================================================

Description
----------------------

Applies bilinear sampling to input feature map.

Bilinear Sampling is the key of  [NIPS2015] \"Spatial Transformer Networks\". The usage of the operator is very similar to remap function in OpenCV,
except that the operator has the backward pass.

Given :math:`data` and :math:`grid`, then the output is computed by

.. math::

  x_{src} = grid[batch, 0, y_{dst}, x_{dst}] \\
  y_{src} = grid[batch, 1, y_{dst}, x_{dst}] \\
  output[batch, channel, y_{dst}, x_{dst}] = G(data[batch, channel, y_{src}, x_{src})

:math:`x_{dst}`, :math:`y_{dst}` enumerate all spatial locations in :math:`output`, and :math:`G()` denotes the bilinear interpolation kernel.
The out-boundary points will be padded with zeros.The shape of the output will be (data.shape[0], data.shape[1], grid.shape[2], grid.shape[3]).

The operator assumes that :math:`data` has 'NCHW' layout and :math:`grid` has been normalized to [-1, 1].

BilinearSampler often cooperates with GridGenerator which generates sampling grids for BilinearSampler.
GridGenerator supports two kinds of transformation: ``affine`` and ``warp``.
If users want to design a CustomOp to manipulate :math:`grid`, please firstly refer to the code of GridGenerator.

Example 1::

	 ## Zoom out data two times
	 data = array([[[[1, 4, 3, 6],
	 [1, 8, 8, 9],
	 [0, 4, 1, 5],
	 [1, 0, 1, 3]]]])
	 
	 affine_matrix = array([[2, 0, 0],
	 [0, 2, 0]])
	 
	 affine_matrix = reshape(affine_matrix, shape=(1, 6))
	 
	 grid = GridGenerator(data=affine_matrix, transform_type='affine', target_shape=(4, 4))
	 
	 out = BilinearSampler(data, grid)
	 
	 out
	 [[[[ 0,   0,     0,   0],
	 [ 0,   3.5,   6.5, 0],
	 [ 0,   1.25,  2.5, 0],
	 [ 0,   0,     0,   0]]]
	 
Example 2::

	 ## shift data horizontally by -1 pixel
	 
	 data = array([[[[1, 4, 3, 6],
	 [1, 8, 8, 9],
	 [0, 4, 1, 5],
	 [1, 0, 1, 3]]]])
	 
	 warp_maxtrix = array([[[[1, 1, 1, 1],
	 [1, 1, 1, 1],
	 [1, 1, 1, 1],
	 [1, 1, 1, 1]],
	 [[0, 0, 0, 0],
	 [0, 0, 0, 0],
	 [0, 0, 0, 0],
	 [0, 0, 0, 0]]]])
	 
	 grid = GridGenerator(data=warp_matrix, transform_type='warp')
	 out = BilinearSampler(data, grid)
	 
	 out
	 [[[[ 4,  3,  6,  0],
	 [ 8,  8,  9,  0],
	 [ 4,  1,  5,  0],
	 [ 0,  1,  3,  0]]]
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input data to the BilinearsamplerOp.                       |
+----------------------------------------+------------------------------------------------------------+
| ``grid``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input grid to the BilinearsamplerOp.grid has two channels: |
|                                        | x_src,                                                     |
|                                        | y_src                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``cudnn.off``                          | boolean or None, optional, default=None                    |
|                                        | whether to turn cudnn off                                  |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/bilinear_sampler.cc#L256


.. disqus::
   :disqus_identifier: mx.nd.BilinearSampler
