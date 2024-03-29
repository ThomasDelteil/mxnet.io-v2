.. raw:: html



``mx.nd.save``
============================

Description
----------------------

Save an mx.nd.array object

**Example**::

	 mat = mx.nd.array(1:3)
	 mx.nd.save(mat, 'temp.mat')
	 mat2 = mx.nd.load('temp.mat')
	 as.array(mat)
	 as.array(mat2[[1]])
	 
	 
Usage
----------

.. code:: r

	mx.nd.save(ndarray, filename)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``ndarray``                            | the ``mx.nd.array`` object                                 |
+----------------------------------------+------------------------------------------------------------+
| ``filename``                           | the filename (including the path)                          |
+----------------------------------------+------------------------------------------------------------+




.. disqus::
   :disqus_identifier: mx.nd.save
