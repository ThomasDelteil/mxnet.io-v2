.. raw:: html



``mx.symbol.load``
====================================

Description
----------------------

Load an mx.symbol object

**Example**::

	 data = mx.symbol.Variable('data')
	 mx.symbol.save(data, 'temp.symbol')
	 data2 = mx.symbol.load('temp.symbol')
	 
	 
Usage
----------

.. code:: r

	mx.symbol.load(filename)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``filename``                           | the filename (including the path)                          |
+----------------------------------------+------------------------------------------------------------+




.. disqus::
   :disqus_identifier: mx.symbol.load
