.. raw:: html



``mx.symbol.SequenceMask``
====================================================

Description
----------------------

Sets all elements outside the sequence to a constant value.

This function takes an n-dimensional input array of the form
[max_sequence_length, batch_size, other_feature_dims] and returns an array of the same shape.

Parameter `sequence_length` is used to handle variable-length sequences. `sequence_length`
should be an input array of positive ints of dimension [batch_size].
To use this parameter, set `use_sequence_length` to `True`,
otherwise each example in the batch is assumed to have the max sequence length and
this operator works as the `identity` operator.

**Example**::
	 
	 x = [[[  1.,   2.,   3.],
	 [  4.,   5.,   6.]],
	 
	 [[  7.,   8.,   9.],
	 [ 10.,  11.,  12.]],
	 
	 [[ 13.,  14.,   15.],
	 [ 16.,  17.,   18.]]]
	 
	 // Batch 1
	 B1 = [[  1.,   2.,   3.],
	 [  7.,   8.,   9.],
	 [ 13.,  14.,  15.]]
	 
	 // Batch 2
	 B2 = [[  4.,   5.,   6.],
	 [ 10.,  11.,  12.],
	 [ 16.,  17.,  18.]]
	 
	 // works as identity operator when sequence_length parameter is not used
	 SequenceMask(x) = [[[  1.,   2.,   3.],
	 [  4.,   5.,   6.]],
	 
	 [[  7.,   8.,   9.],
	 [ 10.,  11.,  12.]],
	 
	 [[ 13.,  14.,   15.],
	 [ 16.,  17.,   18.]]]
	 
	 // sequence_length [1,1] means 1 of each batch will be kept
	 // and other rows are masked with default mask value = 0
	 SequenceMask(x, sequence_length=[1,1], use_sequence_length=True) =
	 [[[  1.,   2.,   3.],
	 [  4.,   5.,   6.]],
	 
	 [[  0.,   0.,   0.],
	 [  0.,   0.,   0.]],
	 
	 [[  0.,   0.,   0.],
	 [  0.,   0.,   0.]]]
	 
	 // sequence_length [2,3] means 2 of batch B1 and 3 of batch B2 will be kept
	 // and other rows are masked with value = 1
	 SequenceMask(x, sequence_length=[2,3], use_sequence_length=True, value=1) =
	 [[[  1.,   2.,   3.],
	 [  4.,   5.,   6.]],
	 
	 [[  7.,   8.,   9.],
	 [  10.,  11.,  12.]],
	 
	 [[   1.,   1.,   1.],
	 [  16.,  17.,  18.]]]
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.SequenceMask(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol                                          |
|                                        | n-dimensional input array of the form                      |
|                                        | [max_sequence_length, batch_size, other_feature_dims]      |
|                                        | where                                                      |
|                                        | n>2                                                        |
+----------------------------------------+------------------------------------------------------------+
| ``sequence.length``                    | NDArray-or-Symbol                                          |
|                                        | vector of sequence lengths of the form [batch_size]        |
+----------------------------------------+------------------------------------------------------------+
| ``use.sequence.length``                | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | If set to true, this layer takes in an extra input         |
|                                        | parameter `sequence_length` to specify variable length     |
|                                        | sequence                                                   |
+----------------------------------------+------------------------------------------------------------+
| ``value``                              | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | The value to be used as a mask.                            |
+----------------------------------------+------------------------------------------------------------+
| ``axis``                               | int, optional, default='0'.                                |
|                                        |                                                            |
|                                        | The sequence axis. Only values of 0 and 1 are currently    |
|                                        | supported.                                                 |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/sequence_mask.cc#L114


.. disqus::
   :disqus_identifier: mx.symbol.SequenceMask
