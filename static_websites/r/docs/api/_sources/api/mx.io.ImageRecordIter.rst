.. raw:: html



``mx.io.ImageRecordIter``
==================================================

Description
----------------------

Iterates on image RecordIO files.  

Reads batches of images from .rec RecordIO files. One can use ``im2rec.py`` tool
(in tools/) to pack raw image files into RecordIO files. This iterator is less
flexible to customization but is fast and has lot of language bindings. To
iterate over raw images directly use ``ImageIter`` instead (in Python).

**Example**::
	 
	 data_iter = mx.io.ImageRecordIter(
	 path_imgrec="./sample.rec", # The target record file.
	 data_shape=(3, 227, 227), # Output data shape; 227x227 region will be cropped from the original image.
	 batch_size=4, # Number of items per batch.
	 resize=256 # Resize the shorter edge to 256 before cropping.
	 # You can specify more augmentation options. Use help(mx.io.ImageRecordIter) to see all the options.
	 )
	 # You can now use the data_iter to access batches of images.
	 batch = data_iter.next() # first batch.
	 images = batch.data[0] # This will contain 4 (=batch_size) images each of 3x227x227.
	 # process the images
	 ...
	 data_iter.reset() # To restart the iterator from the beginning.
	 
	 
	 

Usage
----------

.. code:: r

	mx.io.ImageRecordIter(...)

Arguments
------------------

+----------------------------------------+------------------------------------------------------------+
| Argument                               | Description                                                |
+========================================+============================================================+
| ``path.imglist``                       | string, optional, default=''.                              |
|                                        |                                                            |
|                                        | Path to the image list (.lst) file. Generally created with |
|                                        | tools/im2rec.py. Format (Tab separated): <index of record> |
|                                        | <one or more labels> <relative path from root              |
|                                        | folder>.                                                   |
+----------------------------------------+------------------------------------------------------------+
| ``path.imgrec``                        | string, optional, default=''.                              |
|                                        |                                                            |
|                                        | Path to the image RecordIO (.rec) file or a directory      |
|                                        | path. Created with                                         |
|                                        | tools/im2rec.py.                                           |
+----------------------------------------+------------------------------------------------------------+
| ``path.imgidx``                        | string, optional, default=''.                              |
|                                        |                                                            |
|                                        | Path to the image RecordIO index (.idx) file. Created with |
|                                        | tools/im2rec.py.                                           |
+----------------------------------------+------------------------------------------------------------+
| ``aug.seq``                            | string, optional, default='aug_default'.                   |
|                                        |                                                            |
|                                        | The augmenter names to represent sequence of augmenters to |
|                                        | be applied, seperated by comma. Additional keyword         |
|                                        | parameters will be seen by these                           |
|                                        | augmenters.                                                |
+----------------------------------------+------------------------------------------------------------+
| ``label.width``                        | int, optional, default='1'.                                |
|                                        |                                                            |
|                                        | The number of labels per image.                            |
+----------------------------------------+------------------------------------------------------------+
| ``data.shape``                         | Shape(tuple), required.                                    |
|                                        |                                                            |
|                                        | The shape of one output image in (channels, height, width) |
|                                        | format.                                                    |
+----------------------------------------+------------------------------------------------------------+
| ``preprocess.threads``                 | int, optional, default='4'.                                |
|                                        |                                                            |
|                                        | The number of threads to do preprocessing.                 |
+----------------------------------------+------------------------------------------------------------+
| ``verbose``                            | boolean, optional, default=1.                              |
|                                        |                                                            |
|                                        | If or not output verbose information.                      |
+----------------------------------------+------------------------------------------------------------+
| ``num.parts``                          | int, optional, default='1'.                                |
|                                        |                                                            |
|                                        | Virtually partition the data into these many parts.        |
+----------------------------------------+------------------------------------------------------------+
| ``part.index``                         | int, optional, default='0'.                                |
|                                        |                                                            |
|                                        | The *i*-th virtual partition to be read.                   |
+----------------------------------------+------------------------------------------------------------+
| ``shuffle.chunk.size``                 | , optional, default=0.                                     |
|                                        |                                                            |
|                                        | The data shuffle buffer size in MB. Only valid if shuffle  |
|                                        | is                                                         |
|                                        | true.                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``shuffle.chunk.seed``                 | int, optional, default='0'.                                |
|                                        |                                                            |
|                                        | The random seed for shuffling                              |
+----------------------------------------+------------------------------------------------------------+
| ``shuffle``                            | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Whether to shuffle data randomly or not.                   |
+----------------------------------------+------------------------------------------------------------+
| ``seed``                               | int, optional, default='0'.                                |
|                                        |                                                            |
|                                        | The random seed.                                           |
+----------------------------------------+------------------------------------------------------------+
| ``batch.size``                         | int (non-negative), required.                              |
|                                        |                                                            |
|                                        | Batch size.                                                |
+----------------------------------------+------------------------------------------------------------+
| ``round.batch``                        | boolean, optional, default=1.                              |
|                                        |                                                            |
|                                        | Whether to use round robin to handle overflow batch or     |
|                                        | not.                                                       |
+----------------------------------------+------------------------------------------------------------+
| ``prefetch.buffer``                    | , optional, default=4.                                     |
|                                        |                                                            |
|                                        | Maximum number of batches to prefetch.                     |
+----------------------------------------+------------------------------------------------------------+
| ``dtype``                              | {None, 'float16', 'float32', 'float64', 'int32', 'int64',  |
|                                        | 'uint8'},optional,                                         |
|                                        | default='None'.                                            |
|                                        |                                                            |
|                                        | Output data type. ``None`` means no change.                |
+----------------------------------------+------------------------------------------------------------+
| ``resize``                             | int, optional, default='-1'.                               |
|                                        |                                                            |
|                                        | Down scale the shorter edge to a new size before applying  |
|                                        | other                                                      |
|                                        | augmentations.                                             |
+----------------------------------------+------------------------------------------------------------+
| ``rand.crop``                          | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | If or not randomly crop the image                          |
+----------------------------------------+------------------------------------------------------------+
| ``random.resized.crop``                | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | If or not perform random resized cropping on the image, as |
|                                        | a standard preprocessing for resnet training on ImageNet   |
|                                        | data.                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``max.rotate.angle``                   | int, optional, default='0'.                                |
|                                        |                                                            |
|                                        | Rotate by a random degree in ``[-v, v]``                   |
+----------------------------------------+------------------------------------------------------------+
| ``max.aspect.ratio``                   | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | Change the aspect (namely width/height) to a random value. |
|                                        | If min_aspect_ratio is None then the aspect ratio ins      |
|                                        | sampled from [1 - max_aspect_ratio, 1 + max_aspect_ratio], |
|                                        | else it is in ``[min_aspect_ratio,                         |
|                                        | max_aspect_ratio]``                                        |
+----------------------------------------+------------------------------------------------------------+
| ``min.aspect.ratio``                   | float or None, optional, default=None.                     |
|                                        |                                                            |
|                                        | Change the aspect (namely width/height) to a random value  |
|                                        | in ``[min_aspect_ratio,                                    |
|                                        | max_aspect_ratio]``                                        |
+----------------------------------------+------------------------------------------------------------+
| ``max.shear.ratio``                    | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | Apply a shear transformation (namely ``(x,y)->(x+my,y)``)  |
|                                        | with ``m`` randomly chose from ``[-max_shear_ratio,        |
|                                        | max_shear_ratio]``                                         |
+----------------------------------------+------------------------------------------------------------+
| ``max.crop.size``                      | int, optional, default='-1'.                               |
|                                        |                                                            |
|                                        | Crop both width and height into a random size in           |
|                                        | ``[min_crop_size, max_crop_size].``Ignored if              |
|                                        | ``random_resized_crop`` is                                 |
|                                        | True.                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``min.crop.size``                      | int, optional, default='-1'.                               |
|                                        |                                                            |
|                                        | Crop both width and height into a random size in           |
|                                        | ``[min_crop_size, max_crop_size].``Ignored if              |
|                                        | ``random_resized_crop`` is                                 |
|                                        | True.                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``max.random.scale``                   | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Resize into ``[width*s, height*s]`` with ``s`` randomly    |
|                                        | chosen from ``[min_random_scale, max_random_scale]``.      |
|                                        | Ignored if ``random_resized_crop`` is                      |
|                                        | True.                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``min.random.scale``                   | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Resize into ``[width*s, height*s]`` with ``s`` randomly    |
|                                        | chosen from ``[min_random_scale,                           |
|                                        | max_random_scale]``Ignored if ``random_resized_crop`` is   |
|                                        | True.                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``max.random.area``                    | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Change the area (namely width * height) to a random value  |
|                                        | in ``[min_random_area, max_random_area]``. Ignored if      |
|                                        | ``random_resized_crop`` is                                 |
|                                        | False.                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``min.random.area``                    | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Change the area (namely width * height) to a random value  |
|                                        | in ``[min_random_area, max_random_area]``. Ignored if      |
|                                        | ``random_resized_crop`` is                                 |
|                                        | False.                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``max.img.size``                       | float, optional, default=1e+10.                            |
|                                        |                                                            |
|                                        | Set the maximal width and height after all resize and      |
|                                        | rotate argumentation are                                   |
|                                        | applied                                                    |
+----------------------------------------+------------------------------------------------------------+
| ``min.img.size``                       | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | Set the minimal width and height after all resize and      |
|                                        | rotate argumentation are                                   |
|                                        | applied                                                    |
+----------------------------------------+------------------------------------------------------------+
| ``brightness``                         | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | Add a random value in ``[-brightness, brightness]`` to the |
|                                        | brightness of                                              |
|                                        | image.                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``contrast``                           | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | Add a random value in ``[-contrast, contrast]`` to the     |
|                                        | contrast of                                                |
|                                        | image.                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``saturation``                         | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | Add a random value in ``[-saturation, saturation]`` to the |
|                                        | saturation of                                              |
|                                        | image.                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``pca.noise``                          | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | Add PCA based noise to the image.                          |
+----------------------------------------+------------------------------------------------------------+
| ``random.h``                           | int, optional, default='0'.                                |
|                                        |                                                            |
|                                        | Add a random value in ``[-random_h, random_h]`` to the H   |
|                                        | channel in HSL color                                       |
|                                        | space.                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``random.s``                           | int, optional, default='0'.                                |
|                                        |                                                            |
|                                        | Add a random value in ``[-random_s, random_s]`` to the S   |
|                                        | channel in HSL color                                       |
|                                        | space.                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``random.l``                           | int, optional, default='0'.                                |
|                                        |                                                            |
|                                        | Add a random value in ``[-random_l, random_l]`` to the L   |
|                                        | channel in HSL color                                       |
|                                        | space.                                                     |
+----------------------------------------+------------------------------------------------------------+
| ``rotate``                             | int, optional, default='-1'.                               |
|                                        |                                                            |
|                                        | Rotate by an angle. If set, it overwrites the              |
|                                        | ``max_rotate_angle``                                       |
|                                        | option.                                                    |
+----------------------------------------+------------------------------------------------------------+
| ``fill.value``                         | int, optional, default='255'.                              |
|                                        |                                                            |
|                                        | Set the padding pixels value to ``fill_value``.            |
+----------------------------------------+------------------------------------------------------------+
| ``data.shape``                         | Shape(tuple), required.                                    |
|                                        |                                                            |
|                                        | The shape of a output image.                               |
+----------------------------------------+------------------------------------------------------------+
| ``inter.method``                       | int, optional, default='1'.                                |
|                                        |                                                            |
|                                        | The interpolation method: 0-NN 1-bilinear 2-cubic 3-area   |
|                                        | 4-lanczos4 9-auto                                          |
|                                        | 10-rand.                                                   |
+----------------------------------------+------------------------------------------------------------+
| ``pad``                                | int, optional, default='0'.                                |
|                                        |                                                            |
|                                        | Change size from ``[width, height]`` into ``[pad + width + |
|                                        | pad, pad + height + pad]`` by padding                      |
|                                        | pixes                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``seed.aug``                           | int or None, optional, default='None'.                     |
|                                        |                                                            |
|                                        | Random seed for augmentations.                             |
+----------------------------------------+------------------------------------------------------------+
| ``mirror``                             | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Whether to mirror the image or not. If true, images are    |
|                                        | flipped along the horizontal                               |
|                                        | axis.                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``rand.mirror``                        | boolean, optional, default=0.                              |
|                                        |                                                            |
|                                        | Whether to randomly mirror images or not. If true, 50% of  |
|                                        | the images will be randomly mirrored (flipped along the    |
|                                        | horizontal                                                 |
|                                        | axis)                                                      |
+----------------------------------------+------------------------------------------------------------+
| ``mean.img``                           | string, optional, default=''.                              |
|                                        |                                                            |
|                                        | Filename of the mean image.                                |
+----------------------------------------+------------------------------------------------------------+
| ``mean.r``                             | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | The mean value to be subtracted on the R channel           |
+----------------------------------------+------------------------------------------------------------+
| ``mean.g``                             | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | The mean value to be subtracted on the G channel           |
+----------------------------------------+------------------------------------------------------------+
| ``mean.b``                             | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | The mean value to be subtracted on the B channel           |
+----------------------------------------+------------------------------------------------------------+
| ``mean.a``                             | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | The mean value to be subtracted on the alpha channel       |
+----------------------------------------+------------------------------------------------------------+
| ``std.r``                              | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Augmentation Param: Standard deviation on R channel.       |
+----------------------------------------+------------------------------------------------------------+
| ``std.g``                              | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Augmentation Param: Standard deviation on G channel.       |
+----------------------------------------+------------------------------------------------------------+
| ``std.b``                              | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Augmentation Param: Standard deviation on B channel.       |
+----------------------------------------+------------------------------------------------------------+
| ``std.a``                              | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Augmentation Param: Standard deviation on Alpha channel.   |
+----------------------------------------+------------------------------------------------------------+
| ``scale``                              | float, optional, default=1.                                |
|                                        |                                                            |
|                                        | Multiply the image with a scale value.                     |
+----------------------------------------+------------------------------------------------------------+
| ``max.random.contrast``                | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | Change the contrast with a value randomly chosen from      |
|                                        | ``[-max_random_contrast,                                   |
|                                        | max_random_contrast]``                                     |
+----------------------------------------+------------------------------------------------------------+
| ``max.random.illumination``            | float, optional, default=0.                                |
|                                        |                                                            |
|                                        | Change the illumination with a value randomly chosen from  |
|                                        | ``[-max_random_illumination,                               |
|                                        | max_random_illumination]``                                 |
+----------------------------------------+------------------------------------------------------------+

Value
----------

``iter`` The result mx.dataiter


Link to Source Code: http://github.com/apache/incubator-mxnet/blob/master/src/io/iter_image_recordio_2.cc#L760


.. disqus::
   :disqus_identifier: mx.io.ImageRecordIter
