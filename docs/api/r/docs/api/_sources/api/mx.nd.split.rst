.. raw:: html



``mx.nd.split``
==============================

Description
----------------------

Splits an array along a particular axis into multiple sub-arrays.

.. note:: ``SliceChannel`` is deprecated. Use ``split`` instead.

**Note** that `num_outputs` should evenly divide the length of the axis
along which to split the array.

**Example**::
	 
	 x  = [[[ 1.]
	 [ 2.]]
	 [[ 3.]
	 [ 4.]]
	 [[ 5.]
	 [ 6.]]]
	 x.shape = (3, 2, 1)
	 
	 y = split(x, axis=1, num_outputs=2) // a list of 2 arrays with shape (3, 1, 1)
	 y = [[[ 1.]]
	 [[ 3.]]
	 [[ 5.]]]
	 
	 [[[ 2.]]
	 [[ 4.]]
	 [[ 6.]]]
	 
	 y[0].shape = (3, 1, 1)
	 
	 z = split(x, axis=0, num_outputs=3) // a list of 3 arrays with shape (1, 2, 1)
	 z = [[[ 1.]
	 [ 2.]]]
	 
	 [[[ 3.]
	 [ 4.]]]
	 
	 [[[ 5.]
	 [ 6.]]]
	 
	 z[0].shape = (1, 2, 1)
	 
	 `squeeze_axis=1` removes the axis with length 1 from the shapes of the output arrays.
	 **Note** that setting `squeeze_axis` to ``1`` removes axis with length 1 only
	 along the `axis` which it is split.
	 Also `squeeze_axis` can be set to true only if ``input.shape[axis] == num_outputs``.
	 
**Example**::
	 
	 z = split(x, axis=0, num_outputs=3, squeeze_axis=1) // a list of 3 arrays with shape (2, 1)
	 z = [[ 1.]
	 [ 2.]]
	 
	 [[ 3.]
	 [ 4.]]
	 
	 [[ 5.]
	 [ 6.]]
	 z[0].shape = (2 ,1 )
	 
	 
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The input                                                  |
+----------------------------------------+------------------------------------------------------------+
| ``num.outputs``                        | int, required.                                             |
|                                        |                                                            |
|                                        | Number of splits. Note that this should evenly divide the  |
|                                        | length of the                                              |
|                                        | `axis`.                                                    |
+----------------------------------------+------------------------------------------------------------+
| ``axis``                               | int, optional, default='1'.                                |
|                                        |                                                            |
|                                        | Axis along which to split.                                 |
+----------------------------------------+------------------------------------------------------------+
| ``squeeze.axis``                       | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | If true, Removes the axis with length 1 from the shapes of |
|                                        | the output arrays. **Note** that setting `squeeze_axis` to |
|                                        | ``true`` removes axis with length 1 only along the `axis`  |
|                                        | which it is split. Also `squeeze_axis` can be set to       |
|                                        | ``true`` only if ``input.shape[axis] ==                    |
|                                        | num_outputs``.                                             |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/slice_channel.cc#L107


.. disqus::
   :disqus_identifier: mx.nd.split
