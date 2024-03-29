.. raw:: html



``mx.symbol.gather_nd``
==============================================

Description
----------------------

Gather elements or slices from `data` and store to a tensor whose
shape is defined by `indices`.

Given `data` with shape `(X_0, X_1, ..., X_{N-1})` and indices with shape
`(M, Y_0, ..., Y_{K-1})`, the output will have shape `(Y_0, ..., Y_{K-1}, X_M, ..., X_{N-1})`,
where `M <= N`. If `M == N`, output shape will simply be `(Y_0, ..., Y_{K-1})`.

The elements in output is defined as follows::

	 output[y_0, ..., y_{K-1}, x_M, ..., x_{N-1}] = data[indices[0, y_0, ..., y_{K-1}],
	 ...,
	 indices[M-1, y_0, ..., y_{K-1}],
	 x_M, ..., x_{N-1}]
	 
**Example**::
	 
	 data = [[0, 1], [2, 3]]
	 indices = [[1, 1, 0], [0, 1, 0]]
	 gather_nd(data, indices) = [2, 3, 0]
	 
	 data = [[[1, 2], [3, 4]], [[5, 6], [7, 8]]]
	 indices = [[0, 1], [1, 0]]
	 gather_nd(data, indices) = [[3, 4], [5, 6]]
	 
Usage
----------

.. code:: r

	mx.symbol.gather_nd(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol                                          |
|                                        | data                                                       |
+----------------------------------------+------------------------------------------------------------+
| ``indices``                            | NDArray-or-Symbol                                          |
|                                        | indices                                                    |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol



.. disqus::
   :disqus_identifier: mx.symbol.gather_nd
