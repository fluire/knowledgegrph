- to compare the sample mean to population mean
	- if population standard deviation is known -> z-test
	- other wise -> t-test
| type of test | z or t Statistics             | expected p -value | decision    |
| ------------ | ----------------------------- | ----------------- | ----------- |
| two tailed   | calculated value z or t >1.96 | < 0.05            | reject null |
| one tailed   | calculated value z or t >1.64 | <0.05             | reject null |
- example
	- null hypothesis: µ1 = µ2
	- alternate hypothesis: 
		- these are called the two tailed test
		1. µ1 > µ2 -> right rejection
		2. µ1< µ2 -> left rejection
		3. µ1 != µ2 -> two 

## Equal versus unequal variance
- levenes test: to access the equality of variances.
	- eg:
>null hypothesis: variances are equal
>if the significance values from levenes test is less than 0.05 reject null
```
	use -scipy.stats.leven(col1,col2,center=mean)
	if p-value < α:
		scipy.stats.ttest_ind(col1,col2,equal_var=True)
	else:
		keep equal var to False
```
	