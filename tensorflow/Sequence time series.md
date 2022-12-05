 - univariate and multi variate time series variables
 - ##### things we can do using machine learning in time series
	 - FORECAST future trend
	 - know trends in past time -> imputation ->what the data would have been-> fill up the missing data points.
	 - detect anomalies.
	 - spot patterns -> to analyze sound to know the word said.
- TREND 📈, SEASONALITY☁⛅⛈☁⛅⛈, WHITE NOISE , AUTOCORRERALTED (have previous mem and sudden spikes called innovations), NON-STATIONARY TIME SERIES.
- unlike more data more accuracy non stationary time series requires optimal time window for making accurate predictions.

### Train, Validation and test
- Fixed partitioning -
	- seasonality :- making sure that in one cycle all the seasons are covered
	- ![[Pasted image 20221115101213.png]]
	- you can also train on test data later on as it is the most recent data points in time space.
	- ![[Pasted image 20221115101427.png]]
-  Roll-forward Partitioning:
	- ![[Pasted image 20221115102140.png]]
### Metrics
   - errors -> forecast - actual
   - mse = np.square(error).mean() -> getting rid of negative values
   - rmse = np.sqrt(mse) -> for same scale as the original error
   -  mae = np.abs(error).mean() -> for not penalizing  having great errors as compared to mse where large error are more penalized
   - mape(mean absolute percentage) -> np.abs(errors/x_valid).mean()

- NAIVE FORECAST a baseline forecast by just using the previous value as next value.
### Moving averages and differencing(non deep learning approach) 
- moving average -> a kind of forecasting method(the average of the measurements at time steps 1 to 10 will be the forecast for time step 11, then the average for time steps 2 to 11 will be the forecast for time step 12, and so on.)
- Differencing -> to remove trend and seasonality from time series.
	- we subtract a one cycle period from its previous cyclic period and then use the moving averages then add the value at t-Period to get the original values
	- ![[Pasted image 20221115103922.png]]
	- ![[Pasted image 20221115104007.png]]
	- the forecast is still noisy -> cause of previous ->to remove this noise , we remove noise from previous value -> using moving averages on those previous values
	- ![[Pasted image 20221120142918.png]]
### Trailing versus centered window
 -  centered window is applied to smooth past values using current values in the moving averages but cannot be done for current values as we don't have any future values, so we use trailing window.

##### Week 2 time series using deep learning
-  we use a window as input and the next value as the prediction and we train the model.
- ![[Pasted image 20221126182824.png]]
- the above code take 0 to 9 -> creates a window of 5 numbers -> removes the data points which do not have complete set of five numbers.
- code for creating a dataset with batch
- ![[Pasted image 20221126192712.png]]
```
def windowed_dataset(series, window_size, batch_size, shuffle_buffer):

    """Generates dataset windows

  

    Args:

      series (array of float) - contains the values of the time series

      window_size (int) - the number of time steps to include in the feature

      batch_size (int) - the batch size

      shuffle_buffer(int) - buffer size to use for the shuffle method

  

    Returns:

      dataset (TF Dataset) - TF Dataset containing time windows

    """

    # Generate a TF Dataset from the series values

    dataset = tf.data.Dataset.from_tensor_slices(series)

    # Window the data but only take those with the specified size

    dataset = dataset.window(window_size + 1, shift=1, drop_remainder=True)

    # Flatten the windows by putting its elements in a single batch

    dataset = dataset.flat_map(lambda window: window.batch(window_size + 1))

  

    # Create tuples with features and labels 

    dataset = dataset.map(lambda window: (window[:-1], window[-1]))

  

    # Shuffle the windows

    dataset = dataset.shuffle(shuffle_buffer)

    # Create batches of windows

    dataset = dataset.batch(batch_size).prefetch(1)

    return dataset
```

#### week 3
- its the same cell in different time steps, if input in 4/1 and there are 3  neurons and total time steps in n then output of one RNN with return sequence = true will be -> 4/3/n
- ![[Pasted image 20221203200609.png]]
- ![[Pasted image 20221203200841.png]]
- we add extra lambda layers for dimensional correction as our window function give 2 dimensions we can expand along one dimension as below and in the end scaling the output to consistence in values.
- ![[Pasted image 20221203201525.png]]
- learning from project : 
	- use lr_scheduler to find appropriate learning rate.
```
def adjust_learning_rate():
    
    model = create_uncompiled_model()
    
    lr_schedule = tf.keras.callbacks.LearningRateScheduler(lambda epoch: 1e-6 * 10**(epoch / 20))
    
    ### START CODE HERE
    
    # Select your optimizer
    optimizer = "adam"
    
    # Compile the model passing in the appropriate loss
    model.compile(loss="mae",
                  optimizer=optimizer, 
                  metrics=["mae"]) 
    
    ### END CODE HERE
    
    history = model.fit(dataset, epochs=100, callbacks=[lr_schedule])
    
    return history
	
```

#### week 4
- we can use 1d convolutions to improve the output mae.
- ![[Pasted image 20221204104213.png]]
- 