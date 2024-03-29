.. raw:: html



``mx.symbol.SequenceReverse``
==========================================================

Description
----------------------

Reverses the elements of each sequence.

This function takes an n-dimensional input array of the form [max_sequence_length, batch_size, other_feature_dims]
and returns an array of the same shape.

Parameter `sequence_length` is used to handle variable-length sequences.
`sequence_length` should be an input array of positive ints of dimension [batch_size].
To use this parameter, set `use_sequence_length` to `True`,
otherwise each example in the batch is assumed to have the max sequence length.

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
	 
	 // returns reverse sequence when sequence_length parameter is not used
	 SequenceReverse(x) = [[[ 13.,  14.,   15.],
	 [ 16.,  17.,   18.]],
	 
	 [[  7.,   8.,   9.],
	 [ 10.,  11.,  12.]],
	 
	 [[  1.,   2.,   3.],
	 [  4.,   5.,   6.]]]
	 
	 // sequence_length [2,2] means 2 rows of
	 // both batch B1 and B2 will be reversed.
	 SequenceReverse(x, sequence_length=[2,2], use_sequence_length=True) =
	 [[[  7.,   8.,   9.],
	 [ 10.,  11.,  12.]],
	 
	 [[  1.,   2.,   3.],
	 [  4.,   5.,   6.]],
	 
	 [[ 13.,  14.,   15.],
	 [ 16.,  17.,   18.]]]
	 
	 // sequence_length [2,3] means 2 of batch B2 and 3 of batch B3
	 // will be reversed.
	 SequenceReverse(x, sequence_length=[2,3], use_sequence_length=True) =
	 [[[  7.,   8.,   9.],
	 [ 16.,  17.,  18.]],
	 
	 [[  1.,   2.,   3.],
	 [ 10.,  11.,  12.]],
	 
	 [[ 13.,  14,   15.],
	 [  4.,   5.,   6.]]]
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.SequenceReverse(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol                                          |
|                                        | n-dimensional input array of the form                      |
|                                        | [max_sequence_length, batch_size, other dims] where        |
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
| ``axis``                               | int, optional, default='0'.                                |
|                                        |                                                            |
|                                        | The sequence axis. Only 0 is currently supported.          |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/sequence_reverse.cc#L113


.. disqus::
   :disqus_identifier: mx.symbol.SequenceReverse
