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
### Moving averages and differencing
- moving average -> a kind of forecasting method
- Differencing -> to remove trend and seasonality from time series.
	- we subtract a one cycle period from its previous cyclic period and then use the moving averages then add the value at t-Period to get the original values
	- ![[Pasted image 20221115103922.png]]
	- ![[Pasted image 20221115104007.png]]
	- 