.. raw:: html



``mx.symbol.Pooling_v1``
================================================

Description
----------------------

This operator is DEPRECATED.
Perform pooling on the input.

The shapes for 2-D pooling is

- **data**: *(batch_size, channel, height, width)*
- **out**: *(batch_size, num_filter, out_height, out_width)*, with::

	 out_height = f(height, kernel[0], pad[0], stride[0])
	 out_width = f(width, kernel[1], pad[1], stride[1])
	 
	 The definition of *f* depends on ``pooling_convention``, which has two options:
	 
- **valid** (default)::

	 f(x, k, p, s) = floor((x+2*p-k)/s)+1
	 
- **full**, which is compatible with Caffe::

	 f(x, k, p, s) = ceil((x+2*p-k)/s)+1
	 
	 But ``global_pool`` is set to be true, then do a global pooling, namely reset
	 ``kernel=(height, width)``.
	 
	 Three pooling options are supported by ``pool_type``:
	 
	 - **avg**: average pooling
	 - **max**: max pooling
	 - **sum**: sum pooling
	 
	 1-D pooling is special case of 2-D pooling with *weight=1* and
	 *kernel[1]=1*.
	 
	 For 3-D pooling, an additional *depth* dimension is added before
	 *height*. Namely the input data will have shape *(batch_size, channel, depth,
	 height, width)*.
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.Pooling_v1(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input data to the pooling operator.                        |
+----------------------------------------+------------------------------------------------------------+
| ``kernel``                             | Shape(tuple), optional, default=[].                        |
|                                        |                                                            |
|                                        | pooling kernel size: (y, x) or (d, y, x)                   |
+----------------------------------------+------------------------------------------------------------+
| ``pool.type``                          | {'avg', 'max', 'sum'},optional, default='max'.             |
|                                        |                                                            |
|                                        | Pooling type to be applied.                                |
+----------------------------------------+------------------------------------------------------------+
| ``global.pool``                        | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Ignore kernel size, do global pooling based on current     |
|                                        | input feature                                              |
|                                        | map.                                                       |
+----------------------------------------+------------------------------------------------------------+
| ``pooling.convention``                 | {'full', 'valid'},optional, default='valid'.               |
|                                        |                                                            |
|                                        | Pooling convention to be applied.                          |
+----------------------------------------+------------------------------------------------------------+
| ``stride``                             | Shape(tuple), optional, default=[].                        |
|                                        |                                                            |
|                                        | stride: for pooling (y, x) or (d, y, x)                    |
+----------------------------------------+------------------------------------------------------------+
| ``pad``                                | Shape(tuple), optional, default=[].                        |
|                                        |                                                            |
|                                        | pad for pooling: (y, x) or (d, y, x)                       |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/pooling_v1.cc#L104


.. disqus::
   :disqus_identifier: mx.symbol.Pooling_v1
