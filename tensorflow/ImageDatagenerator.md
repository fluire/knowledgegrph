- so its sometime clumsy task to get a gather data n its labels and load for modeling, so Imagedatagenerator helps to do the same 
````
tf.keras.preprocessing.image.ImageDataGenerator(    featurewise_center=False,    samplewise_center=False,    featurewise_std_normalization=False,    samplewise_std_normalization=False,    zca_whitening=False,    zca_epsilon=1e-06,    rotation_range=0,    width_shift_range=0.0,    height_shift_range=0.0,    brightness_range=None,    shear_range=0.0,    zoom_range=0.0,    channel_shift_range=0.0,    fill_mode='nearest',    cval=0.0,    horizontal_flip=False,    vertical_flip=False,    rescale=None,    preprocessing_function=None,    data_format=None,    validation_split=0.0,    interpolation_order=1,    dtype=None)
````
![[Pasted image 20220910213449.png]]
![[Pasted image 20220910213816.png]]

- why this:
	- consider this storage structure directly give traindir to the method and it will load the data with automatic giving the label human and horse.
	- you can even specify the size and batch of the image and many more options.
	- we can use validation_datagen instead of train_datagen to get a dataset crated for validation and pass it while model .fit().
	- 