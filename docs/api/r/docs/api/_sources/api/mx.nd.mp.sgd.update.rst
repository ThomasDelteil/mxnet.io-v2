.. raw:: html



``mx.nd.mp.sgd.update``
==============================================

Description
----------------------

Updater function for multi-precision sgd optimizer


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``weight``                             | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Weight                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``grad``                               | NDArray-or-Symbol                                          |
|                                        | gradient                                                   |
+----------------------------------------+------------------------------------------------------------+
| ``weight32``                           | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Weight32                                                   |
+----------------------------------------+------------------------------------------------------------+
| ``lr``                                 | float, required.                                           |
|                                        |                                                            |
|                                        | Learning rate                                              |
+----------------------------------------+------------------------------------------------------------+
| ``wd``                                 | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | Weight decay augments the objective function with a        |
|                                        | regularization term that penalizes large weights. The      |
|                                        | penalty scales with the square of the magnitude of each    |
|                                        | weight.                                                    |
+----------------------------------------+------------------------------------------------------------+
| ``rescale.grad``                       | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Rescale gradient to grad = rescale_grad*grad.              |
+----------------------------------------+------------------------------------------------------------+
| ``clip.gradient``                      | float, optional, default=-1.                               |
|                                        |                                                            |
|                                        | Clip gradient to the range of [-clip_gradient,             |
|                                        | clip_gradient] If clip_gradient <= 0, gradient clipping is |
|                                        | turned off. grad = max(min(grad, clip_gradient),           |
|                                        | -clip_gradient).                                           |
+----------------------------------------+------------------------------------------------------------+
| ``lazy.update``                        | boolean, optional, default=1.                              |
|                                        |                                                            |
|                                        | If true, lazy updates are applied if gradient's stype is   |
|                                        | row_sparse.                                                |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray



.. disqus::
   :disqus_identifier: mx.nd.mp.sgd.update
