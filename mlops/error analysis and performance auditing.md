

- error analysis is an iterative process
- Visual inspection
	- specific class
	- image properties
	- other meta data
__we can tag the the noise in data like car noise in audio data__.
- useful metric for each tag
	- what fraction of errors has tag?
	- of all data with that tag, what fraction is misclassified?
	- what fraction of all the data has that data?
	- room for improvement with that tag?
- Prioritizing what to work on 
	- deciding on most important categories to work on based on:
		1. How much room for improvement there is
		2. How frequently that category appears
		3. How easy is to improve accuracy in that category
		4. Hoe important it is to improve in that category
		5. ![[Pasted image 20220714150425.jpg]]
- adding / improving data for specific category

- # skewed dataset
	- analyzing more than accuracy
	- ![[Pasted image 20220724205838.png]]
	 - this way we can check the accuracy of our model with skew data.
	 - now to compare the two different models having different precision and recall we use f1- score - harmonic mean of precision and recall.
	 - ![[Pasted image 20220724210850.png]]

	- for multiclass classification. it also help is determining which class to work on.
	- ![[Pasted image 20220724212941.png]]
- # Performance auditing:
	- Auditing framework
		1. Brainstorming the ways the system might go wrong
			1. performance on subset of data i.e. gender, ethnicity)
			2. how common are certain error i.e. FP, FN
			3. performance on rare classes.
		2. establish metric to assess performance against these issues on a slice of dataset.
		3. get business to buy in / make them understand the above issues.