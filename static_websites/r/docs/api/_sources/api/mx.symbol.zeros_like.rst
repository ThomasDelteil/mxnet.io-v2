.. raw:: html



``mx.symbol.zeros_like``
================================================

Description
----------------------

Return an array of zeros with the same shape, type and storage type
as the input array.

The storage type of ``zeros_like`` output depends on the storage type of the input

- zeros_like(row_sparse) = row_sparse
- zeros_like(csr) = csr
- zeros_like(default) = default

**Example**::
	 
	 x = [[ 1.,  1.,  1.],
	 [ 1.,  1.,  1.]]
	 
	 zeros_like(x) = [[ 0.,  0.,  0.],
	 [ 0.,  0.,  0.]]
	 
Usage
----------

.. code:: r

	mx.symbol.zeros_like(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The input                                                  |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol



.. disqus::
   :disqus_identifier: mx.symbol.zeros_like
