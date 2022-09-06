## Data centric approach shows on how to improve data keeping the code/model unchanged.
- ## data augmentation :
	- improving the one type of data also improves the other kind which are similar like **rubber sheet**![[Pasted image 20220724223250.png]]
	- Goal:
		- create realistic augmentation of data that humans do well on but algorithm does poorly.
	- checklist:
		- does it sound  realistic?
		- is the x->y mapping clear?
		- is the algorithm currently doing poorly on it?
	![[Pasted image 20220727120443.png]]
	- # can adding data hurt?
		- for an unstructured data containing 1. model is large(low bias) 2. the mapping x->y is clear THEN ADDING DATA RARELY HURTS.
		- you can specific features for structured data.
- # Experiment tracking
	- what to track:
		- algorithm / code versioning
		- dataset used.
		- Hyperparameters results
		- Results
	- where:
		- text
		- excel sheet
		- ETS -experiment tracking system
	- desirable features:
		- information needed to replicate the result.
		- summary metric analysis
		- resource monitoring visualization and error analysis.
	