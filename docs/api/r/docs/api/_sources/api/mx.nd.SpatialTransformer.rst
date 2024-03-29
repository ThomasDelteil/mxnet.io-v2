.. raw:: html



``mx.nd.SpatialTransformer``
========================================================

Description
----------------------

Applies a spatial transformer to input feature map.


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Input data to the SpatialTransformerOp.                    |
+----------------------------------------+------------------------------------------------------------+
| ``loc``                                | NDArray-or-Symbol                                          |
|                                        | localisation net, the output dim should be 6 when          |
|                                        | transform_type is affine. You shold initialize the weight  |
|                                        | and bias with identity                                     |
|                                        | tranform.                                                  |
+----------------------------------------+------------------------------------------------------------+
| ``target.shape``                       | Shape(tuple), optional, default=[0,0].                     |
|                                        |                                                            |
|                                        | output shape(h, w) of spatial transformer: (y, x)          |
+----------------------------------------+------------------------------------------------------------+
| ``transform.type``                     | {'affine'}, required.                                      |
|                                        |                                                            |
|                                        | transformation type                                        |
+----------------------------------------+------------------------------------------------------------+
| ``sampler.type``                       | {'bilinear'}, required.                                    |
|                                        |                                                            |
|                                        | sampling type                                              |
+----------------------------------------+------------------------------------------------------------+
| ``cudnn.off``                          | boolean or None, optional, default=None                    |
|                                        | whether to turn cudnn off                                  |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray



.. disqus::
   :disqus_identifier: mx.nd.SpatialTransformer
