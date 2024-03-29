.. raw:: html



``mx.nd.ROIPooling``
========================================

Description
----------------------

Performs region of interest(ROI) pooling on the input array.

ROI pooling is a variant of a max pooling layer, in which the output size is fixed and
region of interest is a parameter. Its purpose is to perform max pooling on the inputs
of non-uniform sizes to obtain fixed-size feature maps. ROI pooling is a neural-net
layer mostly used in training a `Fast R-CNN` network for object detection.

This operator takes a 4D feature map as an input array and region proposals as `rois`,
then it pools over sub-regions of input and produces a fixed-sized output array
regardless of the ROI size.

To crop the feature map accordingly, you can resize the bounding box coordinates
by changing the parameters `rois` and `spatial_scale`.

The cropped feature maps are pooled by standard max pooling operation to a fixed size output
indicated by a `pooled_size` parameter. batch_size will change to the number of region
bounding boxes after `ROIPooling`.

The size of each region of interest doesn't have to be perfectly divisible by
the number of pooling sections(`pooled_size`).

**Example**::
	 
	 x = [[[[  0.,   1.,   2.,   3.,   4.,   5.],
	 [  6.,   7.,   8.,   9.,  10.,  11.],
	 [ 12.,  13.,  14.,  15.,  16.,  17.],
	 [ 18.,  19.,  20.,  21.,  22.,  23.],
	 [ 24.,  25.,  26.,  27.,  28.,  29.],
	 [ 30.,  31.,  32.,  33.,  34.,  35.],
	 [ 36.,  37.,  38.,  39.,  40.,  41.],
	 [ 42.,  43.,  44.,  45.,  46.,  47.]]]]
	 
	 // region of interest i.e. bounding box coordinates.
	 y = [[0,0,0,4,4]]
	 
	 // returns array of shape (2,2) according to the given roi with max pooling.
	 ROIPooling(x, y, (2,2), 1.0) = [[[[ 14.,  16.],
	 [ 26.,  28.]]]]
	 
	 // region of interest is changed due to the change in `spacial_scale` parameter.
	 ROIPooling(x, y, (2,2), 0.7) = [[[[  7.,   9.],
	 [ 19.,  21.]]]]
	 
	 
	 


Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``data``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | The input array to the pooling operator, a 4D Feature      |
|                                        | maps                                                       |
+----------------------------------------+------------------------------------------------------------+
| ``rois``                               | NDArray-or-Symbol.                                         |
|                                        |                                                            |
|                                        | Bounding box coordinates, a 2D array of [[batch_index, x1, |
|                                        | y1, x2, y2]], where (x1, y1) and (x2, y2) are top left and |
|                                        | bottom right corners of designated region of interest.     |
|                                        | `batch_index` indicates the index of corresponding image   |
|                                        | in the input                                               |
|                                        | array                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``pooled.size``                        | Shape(tuple), required.                                    |
|                                        |                                                            |
|                                        | ROI pooling output shape (h,w)                             |
+----------------------------------------+------------------------------------------------------------+
| ``spatial.scale``                      | float, required.                                           |
|                                        |                                                            |
|                                        | Ratio of input feature map height (or w) to raw image      |
|                                        | height (or w). Equals the reciprocal of total stride in    |
|                                        | convolutional                                              |
|                                        | layers                                                     |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``out`` The result mx.ndarray


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/operator/roi_pooling.cc#L295


.. disqus::
   :disqus_identifier: mx.nd.ROIPooling
