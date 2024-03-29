.. raw:: html



``mx.symbol.elemwise_add``
====================================================

Description
----------------------

Adds arguments element-wise.

The storage type of ``elemwise_add`` output depends on storage types of inputs

- elemwise_add(row_sparse, row_sparse) = row_sparse
   - elemwise_add(csr, csr) = csr
   - elemwise_add(default, csr) = default
   - elemwise_add(csr, default) = default
   - elemwise_add(default, rsp) = default
   - elemwise_add(rsp, default) = default
   - otherwise, ``elemwise_add`` generates output with default storage

Usage
----------

.. code:: r

	mx.symbol.elemwise_add(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``lhs``                                | NDArray-or-Symbol                                          |
|                                        | first input                                                |
+----------------------------------------+------------------------------------------------------------+
| ``rhs``                                | NDArray-or-Symbol                                          |
|                                        | second input                                               |
+----------------------------------------+------------------------------------------------------------+
| ``name``                               | string, optional.                                          |
|                                        |                                                            |
|                                        | Name of the resulting symbol.                              |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.symbol



.. disqus::
   :disqus_identifier: mx.symbol.elemwise_add
