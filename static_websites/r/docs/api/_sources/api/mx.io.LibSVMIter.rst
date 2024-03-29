.. raw:: html



``mx.io.LibSVMIter``
========================================

Description
----------------------

Returns the LibSVM iterator which returns data with `csr`
storage type. This iterator is experimental and should be used with care.

The input data is stored in a format similar to LibSVM file format, except that the **indices
are expected to be zero-based instead of one-based, and the column indices for each row are
expected to be sorted in ascending order**. Details of the LibSVM format are available
`here. <https://www.csie.ntu.edu.tw/~cjlin/libsvmtools/datasets/>`_

The `data_shape` parameter is used to set the shape of each line of the data.
The dimension of both `data_shape` and `label_shape` are expected to be 1.

The `data_libsvm` parameter is used to set the path input LibSVM file.
When it is set to a directory, all the files in the directory will be read.

When `label_libsvm` is set to ``NULL``, both data and label are read from the file specified
by `data_libsvm`. In this case, the data is stored in `csr` storage type, while the label is a 1D
dense array.

The `LibSVMIter` only support `round_batch` parameter set to ``True``. Therefore, if `batch_size`
is 3 and there are 4 total rows in libsvm file, 2 more examples are consumed at the first round.

When `num_parts` and `part_index` are provided, the data is split into `num_parts` partitions,
and the iterator only reads the `part_index`-th partition. However, the partitions are not
guaranteed to be even.

``reset()`` is expected to be called only after a complete pass of data.

**Example**::
	 
	 # Contents of libsvm file ``data.t``.
	 1.0 0:0.5 2:1.2
	 -2.0
	 -3.0 0:0.6 1:2.4 2:1.2
	 4 2:-1.2
	 
	 # Creates a `LibSVMIter` with `batch_size`=3.
	 >>> data_iter = mx.io.LibSVMIter(data_libsvm = 'data.t', data_shape = (3,), batch_size = 3)
	 # The data of the first batch is stored in csr storage type
	 >>> batch = data_iter.next()
	 >>> csr = batch.data[0]
	 <CSRNDArray 3x3 @cpu(0)>
	 >>> csr.asnumpy()
	 [[ 0.5        0.          1.2 ]
	 [ 0.          0.          0.  ]
	 [ 0.6         2.4         1.2]]
	 # The label of first batch
	 >>> label = batch.label[0]
	 >>> label
	 [ 1. -2. -3.]
	 <NDArray 3 @cpu(0)>
	 
	 >>> second_batch = data_iter.next()
	 # The data of the second batch
	 >>> second_batch.data[0].asnumpy()
	 [[ 0.          0.         -1.2 ]
	 [ 0.5         0.          1.2 ]
	 [ 0.          0.          0. ]]
	 # The label of the second batch
	 >>> second_batch.label[0].asnumpy()
	 [ 4.  1. -2.]
	 
	 >>> data_iter.reset()
	 # To restart the iterator for the second pass of the data
	 
	 When `label_libsvm` is set to the path to another LibSVM file,
	 data is read from `data_libsvm` and label from `label_libsvm`.
	 In this case, both data and label are stored in the csr format.
	 If the label column in the `data_libsvm` file is ignored.
	 
**Example**::
	 
	 # Contents of libsvm file ``label.t``
	 1.0
	 -2.0 0:0.125
	 -3.0 2:1.2
	 4 1:1.0 2:-1.2
	 
	 # Creates a `LibSVMIter` with specified label file
	 >>> data_iter = mx.io.LibSVMIter(data_libsvm = 'data.t', data_shape = (3,),
	 label_libsvm = 'label.t', label_shape = (3,), batch_size = 3)
	 
	 # Both data and label are in csr storage type
	 >>> batch = data_iter.next()
	 >>> csr_data = batch.data[0]
	 <CSRNDArray 3x3 @cpu(0)>
	 >>> csr_data.asnumpy()
	 [[ 0.5         0.          1.2  ]
	 [ 0.          0.          0.   ]
	 [ 0.6         2.4         1.2 ]]
	 >>> csr_label = batch.label[0]
	 <CSRNDArray 3x3 @cpu(0)>
	 >>> csr_label.asnumpy()
	 [[ 0.          0.          0.   ]
	 [ 0.125       0.          0.   ]
	 [ 0.          0.          1.2 ]]
	 
	 
	 

Usage
----------

.. code:: r

	mx.io.LibSVMIter(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data.libsvm``                        | string, required.                                          |
|                                        |                                                            |
|                                        | The input zero-base indexed LibSVM data file or a          |
|                                        | directory                                                  |
|                                        | path.                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``data.shape``                         | Shape(tuple), required.                                    |
|                                        |                                                            |
|                                        | The shape of one example.                                  |
+----------------------------------------+------------------------------------------------------------+
| ``label.libsvm``                       | string, optional, default='NULL'.                          |
|                                        |                                                            |
|                                        | The input LibSVM label file or a directory path. If NULL,  |
|                                        | all labels will be read from                               |
|                                        | ``data_libsvm``.                                           |
+----------------------------------------+------------------------------------------------------------+
| ``label.shape``                        | Shape(tuple), optional, default=[1].                       |
|                                        |                                                            |
|                                        | The shape of one label.                                    |
+----------------------------------------+------------------------------------------------------------+
| ``num.parts``                          | int, optional, default='1'.                                |
|                                        |                                                            |
|                                        | partition the data into multiple parts                     |
+----------------------------------------+------------------------------------------------------------+
| ``part.index``                         | int, optional, default='0'.                                |
|                                        |                                                            |
|                                        | the index of the part will read                            |
+----------------------------------------+------------------------------------------------------------+
| ``batch.size``                         | int (non-negative), required.                              |
|                                        |                                                            |
|                                        | Batch size.                                                |
+----------------------------------------+------------------------------------------------------------+
| ``round.batch``                        | boolean, optional, default=1.                              |
|                                        |                                                            |
|                                        | Whether to use round robin to handle overflow batch or     |
|                                        | not.                                                       |
+----------------------------------------+------------------------------------------------------------+
| ``prefetch.buffer``                    | , optional, default=4.                                     |
|                                        |                                                            |
|                                        | Maximum number of batches to prefetch.                     |
+----------------------------------------+------------------------------------------------------------+
| ``dtype``                              | {None, 'float16', 'float32', 'float64', 'int32', 'int64',  |
|                                        | 'uint8'},optional,                                         |
|                                        | default='None'.                                            |
|                                        |                                                            |
|                                        | Output data type. ``None`` means no change.                |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``iter`` The result mx.dataiter


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/io/iter_libsvm.cc#L298


.. disqus::
   :disqus_identifier: mx.io.LibSVMIter
