- comparing two variables 
- [[Types of Data]] need to know type of variables
	- Categorical -> Chi square test-> start with cross tab
	- Continuous variable -> pearson correlation test->start with scatter plot
- Chi square test:
	- state your hypo
		Eg
		- h0: there is no association between gender and being tenured
		- ha: there is an association between gender and being tenured
	1. cross tabulation:
		- ![[Pasted image 20220616194257.jpg]]
		- calculate x^2 then use the chi square table and see if the p value is less than or greater then significance level.
		```
		use scipy.stats.chi2_contigency(cont_table, correction = False)
		```

- pearson Correlation test:
	-  state you hypo
		Eg
		- h0 -> there is no correlation between an instructor's beauty score and their evaluation score
		- ha-> there is a correlation between an instructor's beauty score and their teaching evaluation score.
	- plot the scatter plot of two variable
	```
	scipy.stats.pearsonr(var1,var2)
	```

Summary
- Hypothesis testing:
	- purpose: Given sample and an apparent effect, what is the probability of seeing such an effect by chance?
- Example (when one value is categorical and one is continuous)
	1.  stating the hypothesis:
			- H0 : there is no difference between the eval score based on gender.
			- H1 : there is a difference in evaluation score based on gender.
		1. performing the levens test to check the equality of variance, if p> 0.05, variance are equal.
		2.  then do the t-test to test the hypothesis.
	2. ANOVA test cannot work with continuous variable.
		1. like converting the age to age groups -> adding an extra column having the categorical values
		2. Stating the hypothesis:
			1. H0: the three population means are equal
			2. H1: at least one of the mean differ
		3. first do the levens test to check h equivalence of the variance
		4. separate the samples
		5. conduct the ANOVA test -> you get a f score and a p value to conclude the hypothesis.
	3. Chi-square (for categorical data)
		1. state the hypothesis:
			- H0 -> the proportion of teachers who tenured is independent of gender.
			- H1 -> the proportion of teachers who tenured is associated with gender.
		2. creating a cross table.(pd.crosstab(col1,col2))
		3. apply the chi squared test : (scipy.stats.chi2_contigency(cont_table,correction = True)) -> returned value x2, p-value, degree of freedom, expected values.
		4. conclude the hypothesis
	4. correlation : (between two continuous variable) pearsons test
		1. State the hypothesis (Example)
			- H0 -> teaching evaluation not related with the beauty score
			- H1 -> teaching evaluation related with the beauty score
		2. conduct pearsons test ( scipy.stats.pearsonr(ratings_df['beauty'],ratings_df['eval']))
	 
		