.. raw:: html



``mx.symbol.ctc_loss``
============================================

Description
----------------------

Connectionist Temporal Classification Loss.

.. note:: The existing alias ``contrib_CTCLoss`` is deprecated.

The shapes of the inputs and outputs:

	- **data**: `(sequence_length, batch_size, alphabet_size)`
	- **label**: `(batch_size, label_sequence_length)`
	- **out**: `(batch_size)`

The `data` tensor consists of sequences of activation vectors (without applying softmax),
with i-th channel in the last dimension corresponding to i-th label
for i between 0 and alphabet_size-1 (i.e always 0-indexed).
Alphabet size should include one additional value reserved for blank label.
When `blank_label` is ``"first"``, the ``0``-th channel is be reserved for
activation of blank label, or otherwise if it is "last", ``(alphabet_size-1)``-th channel should be
reserved for blank label.

``label`` is an index matrix of integers. When `blank_label` is ``"first"``,
the value 0 is then reserved for blank label, and should not be passed in this matrix. Otherwise,
when `blank_label` is ``"last"``, the value `(alphabet_size-1)` is reserved for blank label.

If a sequence of labels is shorter than *label_sequence_length*, use the special
padding value at the end of the sequence to conform it to the correct
length. The padding value is `0` when `blank_label` is ``"first"``, and `-1` otherwise.

For example, suppose the vocabulary is `[a, b, c]`, and in one batch we have three sequences
'ba', 'cbb', and 'abac'. When `blank_label` is ``"first"``, we can index the labels as
`{'a': 1, 'b': 2, 'c': 3}`, and we reserve the 0-th channel for blank label in data tensor.
The resulting `label` tensor should be padded to be::

	 [[2, 1, 0, 0], [3, 2, 2, 0], [1, 2, 1, 3]]
	 
	 When `blank_label` is ``"last"``, we can index the labels as
	 `{'a': 0, 'b': 1, 'c': 2}`, and we reserve the channel index 3 for blank label in data tensor.
The resulting `label` tensor should be padded to be::

	 [[1, 0, -1, -1], [2, 1, 1, -1], [0, 1, 0, 2]]
	 
	 ``out`` is a list of CTC loss values, one per example in the batch.
	 
	 See *Connectionist Temporal Classification: Labelling Unsegmented
	 Sequence Data with Recurrent Neural Networks*, A. Graves *et al*. for more
	 information on the definition and the algorithm.
	 
	 
	 

Usage
----------

.. code:: r

	mx.symbol.ctc_loss(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input ndarray                                              |
+----------------------------------------+------------------------------------------------------------+
| ``label``                              | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Ground-truth labels for the loss.                          |
+----------------------------------------+------------------------------------------------------------+
| ``data.lengths``                       | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Lengths of data for each of the samples. Only required     |
|                                        | when use_data_lengths is                                   |
|                                        | true.                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``label.lengths``                      | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Lengths of labels for each of the samples. Only required   |
|                                        | when use_label_lengths is                                  |
|                                        | true.                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``use.data.lengths``                   | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Whether the data lenghts are decided by `data_lengths`. If |
|                                        | false, the lengths are equal to the max sequence           |
|                                        | length.                                                    |
+----------------------------------------+------------------------------------------------------------+
| ``use.label.lengths``                  | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Whether the label lenghts are decided by `label_lengths`,  |
|                                        | or derived from `padding_mask`. If false, the lengths are  |
|                                        | derived from the first occurrence of the value of          |
|                                        | `padding_mask`. The value of `padding_mask` is ``0`` when  |
|                                        | first CTC label is reserved for blank, and ``-1`` when     |
|                                        | last label is reserved for blank. See                      |
|                                        | `blank_label`.                                             |
+----------------------------------------+------------------------------------------------------------+
| ``blank.label``                        | {'first', 'last'},optional, default='first'.               |
|                                        |                                                            |
|                                        | Set the label that is reserved for blank label.If "first", |
|                                        | 0-th label is reserved, and label values for tokens in the |
|                                        | vocabulary are between ``1`` and ``alphabet_size-1``, and  |
|                                        | the padding mask is ``-1``. If "last", last label value    |
|                                        | ``alphabet_size-1`` is reserved for blank label instead,   |
|                                        | and label values for tokens in the vocabulary are between  |
|                                        | ``0`` and ``alphabet_size-2``, and the padding mask is     |
|                                        | ``0``.                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/nn/ctc_loss.cc#L100


.. disqus::
   :disqus_identifier: mx.symbol.ctc_loss
