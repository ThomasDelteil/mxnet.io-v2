.. raw:: html



``mx.symbol.Convolution``
==================================================

Description
----------------------

Compute *N*-D convolution on *(N+2)*-D input.

In the 2-D convolution, given input data with shape *(batch_size,
channel, height, width)*, the output is computed by

.. math::

	out[n,i,:,:] = bias[i] + \sum_{j=0}^{channel} data[n,j,:,:] \star
   weight[i,j,:,:]

where :math:`\star` is the 2-D cross-correlation operator.

For general 2-D convolution, the shapes are

- **data**: *(batch_size, channel, height, width)*
- **weight**: *(num_filter, channel, kernel[0], kernel[1])*
- **bias**: *(num_filter,)*
- **out**: *(batch_size, num_filter, out_height, out_width)*.

Define::

	 f(x,k,p,s,d) = floor((x+2*p-d*(k-1)-1)/s)+1
	 
then we have::

	 out_height=f(height, kernel[0], pad[0], stride[0], dilate[0])
	 out_width=f(width, kernel[1], pad[1], stride[1], dilate[1])
	 
	 If ``no_bias`` is set to be true, then the ``bias`` term is ignored.
	 
	 The default data ``layout`` is *NCHW*, namely *(batch_size, channel, height,
	 width)*. We can choose other layouts such as *NWC*.
	 
	 If ``num_group`` is larger than 1, denoted by *g*, then split the input ``data``
	 evenly into *g* parts along the channel axis, and also evenly split ``weight``
	 along the first dimension. Next compute the convolution on the *i*-th part of
	 the data with the *i*-th weight part. The output is obtained by concatenating all
	 the *g* results.
	 
	 1-D convolution does not have *height* dimension but only *width* in space.
	 
	 - **data**: *(batch_size, channel, width)*
	 - **weight**: *(num_filter, channel, kernel[0])*
	 - **bias**: *(num_filter,)*
	 - **out**: *(batch_size, num_filter, out_width)*.
	 
	 3-D convolution adds an additional *depth* dimension besides *height* and
	 *width*. The shapes are
	 
	 - **data**: *(batch_size, channel, depth, height, width)*
	 - **weight**: *(num_filter, channel, kernel[0], kernel[1], kernel[2])*
	 - **bias**: *(num_filter,)*
	 - **out**: *(batch_size, num_filter, out_depth, out_height, out_width)*.
	 
	 Both ``weight`` and ``bias`` are learnable parameters.
	 
	 There are other options to tune the performance.
	 
	 - **cudnn_tune**: enable this option leads to higher startup time but may give
	 faster speed. Options are
	 
	 - **off**: no tuning
	 - **limited_workspace**:run test and pick the fastest algorithm that doesn't
	 exceed workspace limit.
	 - **fastest**: pick the fastest algorithm and ignore workspace limit.
	 - **None** (default): the behavior is determined by environment variable
	 ``MXNET_CUDNN_AUTOTUNE_DEFAULT``. 0 for off, 1 for limited workspace
	 (default), 2 for fastest.
	 
	 - **workspace**: A large number leads to more (GPU) memory usage but may improve
	 the performance.
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.Convolution(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input data to the ConvolutionOp.                           |
+----------------------------------------+------------------------------------------------------------+
| ``weight``                             | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Weight matrix.                                             |
+----------------------------------------+------------------------------------------------------------+
| ``bias``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Bias parameter.                                            |
+----------------------------------------+------------------------------------------------------------+
| ``kernel``                             | Shape(tuple), required.                                    |
|                                        |                                                            |
|                                        | Convolution kernel size: (w,), (h, w) or (d, h, w)         |
+----------------------------------------+------------------------------------------------------------+
| ``stride``                             | Shape(tuple), optional, default=[].                        |
|                                        |                                                            |
|                                        | Convolution stride: (w,), (h, w) or (d, h, w). Defaults to |
|                                        | 1 for each                                                 |
|                                        | dimension.                                                 |
+----------------------------------------+------------------------------------------------------------+
| ``dilate``                             | Shape(tuple), optional, default=[].                        |
|                                        |                                                            |
|                                        | Convolution dilate: (w,), (h, w) or (d, h, w). Defaults to |
|                                        | 1 for each                                                 |
|                                        | dimension.                                                 |
+----------------------------------------+------------------------------------------------------------+
| ``pad``                                | Shape(tuple), optional, default=[].                        |
|                                        |                                                            |
|                                        | Zero pad for convolution: (w,), (h, w) or (d, h, w).       |
|                                        | Defaults to no                                             |
|                                        | padding.                                                   |
+----------------------------------------+------------------------------------------------------------+
| ``num.filter``                         | int (non-negative), required.                              |
|                                        |                                                            |
|                                        | Convolution filter(channel) number                         |
+----------------------------------------+------------------------------------------------------------+
| ``num.group``                          | int (non-negative), optional, default=1.                   |
|                                        |                                                            |
|                                        | Number of group partitions.                                |
+----------------------------------------+------------------------------------------------------------+
| ``workspace``                          | long (non-negative), optional, default=1024.               |
|                                        |                                                            |
|                                        | Maximum temporary workspace allowed (MB) in                |
|                                        | convolution.This parameter has two usages. When CUDNN is   |
|                                        | not used, it determines the effective batch size of the    |
|                                        | convolution kernel. When CUDNN is used, it controls the    |
|                                        | maximum temporary storage used for tuning the best CUDNN   |
|                                        | kernel when `limited_workspace` strategy is                |
|                                        | used.                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``no.bias``                            | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Whether to disable bias parameter.                         |
+----------------------------------------+------------------------------------------------------------+
| ``cudnn.tune``                         | {None, 'fastest', 'limited_workspace', 'off'},optional,    |
|                                        | default='None'.                                            |
|                                        |                                                            |
|                                        | Whether to pick convolution algo by running performance    |
|                                        | test.                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``cudnn.off``                          | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Turn off cudnn for this layer.                             |
+----------------------------------------+------------------------------------------------------------+
| ``layout``                             | {None, 'NCDHW', 'NCHW', 'NCW', 'NDHWC', 'NHWC'},optional,  |
|                                        | default='None'.                                            |
|                                        |                                                            |
|                                        | Set layout for input, output and weight. Empty for         |
|                                        | default layout: NCW for 1d, NCHW for 2d and NCDHW for      |
|                                        | 3d.NHWC and NDHWC are only supported on                    |
|                                        | GPU.                                                       |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/nn/convolution.cc#L461


.. disqus::
   :disqus_identifier: mx.symbol.Convolution
