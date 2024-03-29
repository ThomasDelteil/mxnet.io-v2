.. raw:: html



``mx.nd.dot``
==========================

Description
----------------------

Dot product of two arrays.

``dot``'s behavior depends on the input array dimensions:

	- 1-D arrays: inner product of vectors
	- 2-D arrays: matrix multiplication
	- N-D arrays: a sum product over the last axis of the first input and the first
  axis of the second input

For example, given 3-D ``x`` with shape `(n,m,k)` and ``y`` with shape `(k,r,s)`, the
  result array will have shape `(n,m,r,s)`. It is computed by::

	 dot(x,y)[i,j,a,b] = sum(x[i,j,:]*y[:,a,b])
	 
**Example**::
	 
	 x = reshape([0,1,2,3,4,5,6,7], shape=(2,2,2))
	 y = reshape([7,6,5,4,3,2,1,0], shape=(2,2,2))
	 dot(x,y)[0,0,1,1] = 0
	 sum(x[0,0,:]*y[:,1,1]) = 0
	 
	 The storage type of ``dot`` output depends on storage types of inputs, transpose option and
	 forward_stype option for output storage type. Implemented sparse operations include:
	 
	- dot(default, default, transpose_a=True/False, transpose_b=True/False) = default
	- dot(csr, default, transpose_a=True) = default
	- dot(csr, default, transpose_a=True) = row_sparse
	- dot(csr, default) = default
	- dot(csr, row_sparse) = default
	- dot(default, csr) = csr (CPU only)
	- dot(default, csr, forward_stype='default') = default
	- dot(default, csr, transpose_b=True, forward_stype='default') = default
	 
	 If the combination of input storage types and forward_stype does not match any of the
	 above patterns, ``dot`` will fallback and generate output with default storage.
	 
.. Note::

	 If the storage type of the lhs is "csr", the storage type of gradient w.r.t rhs will be
	 "row_sparse". Only a subset of optimizers support sparse gradients, including SGD, AdaGrad
	 and Adam. Note that by default lazy updates is turned on, which may perform differently
	 from standard updates. For more details, please check the Optimization API at:
	 https://mxnet.incubator.apache.org/api/python/optimization/optimization.html
	 
	 
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``lhs``                                | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The first input                                            |
+----------------------------------------+------------------------------------------------------------+
| ``rhs``                                | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The second input                                           |
+----------------------------------------+------------------------------------------------------------+
| ``transpose.a``                        | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | If true then transpose the first input before dot.         |
+----------------------------------------+------------------------------------------------------------+
| ``transpose.b``                        | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | If true then transpose the second input before dot.        |
+----------------------------------------+------------------------------------------------------------+
| ``forward.stype``                      | {None, 'csr', 'default', 'row_sparse'},optional,           |
|                                        | default='None'.                                            |
|                                        |                                                            |
|                                        | The desired storage type of the forward output given by    |
|                                        | user, if thecombination of input storage types and this    |
|                                        | hint does not matchany implemented ones, the dot operator  |
|                                        | will perform fallback operationand still produce an output |
|                                        | of the desired storage                                     |
|                                        | type.                                                      |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/tensor/dot.cc#L77


.. disqus::
   :disqus_identifier: mx.nd.dot
