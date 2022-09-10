- #  data definition is hard...
	- might be the different kind of right labeling for the same image leading to ambiguity.
	- ![[Pasted image 20220801190536.png]]
	- different labeling for audio clips.
- # overcoming
	- Data definition questions?
		- what is the input x? -> lighting? Contrast? Resolution?
		- What features need to be included?
		- what the target label y.
# major types of data problem...
	![[Pasted image 20220801190652.png]]
	- unstructured : 
		-  may or may not large unlabeled inputs
		-  Human can label more data
		- data augmentation more likely to be helpful.
	- structured data:
		- may be more difficult to obtain more data.
		- human labeling may not be possible.
	- small dataset:
		- clean label are critical.
		- can manually look through dataset and fix label.
		- can get the labelers to talk to each other.
	- big data:
		- Emphasis data process.
	 
| None  | structured | unstructured |
| ----- | ---------- | ------------ |
| small |            |              |
| big   |            |              |
- # small data and labelling consistency..
		- consistency is important while labeling . 
		- ![[Pasted image 20220801190821.png]]
		- # how to improve label consistency:
			1. Have multiple labelers label same example.
			2. for disagreement, have MLE, subject matter expert (SME) or labeler discuss definition of y to reach agreement.
			3. if labelers believe that x doesn't contain enough information, consider changing x.
			4. Iterate until it is hard to significantly increase agreement.
			5. have a class/label to capture uncertainty.
	- # HLP (human level performance):
		- why? -> Estimate Bayes error / irreducible error to help with error analysis and prioritization.
		- In academia, establish and beat a respectable benchmark to support publication.
		- help in establish a more reasonable target.
		- to prove that my/ this model is superior to humans doing the job and thus be adopted.
		-  But rather increase the HLP performance will lead to push the model accuracy.
		- defining the condition for ground truth may increase the HLP to 100% and then becomes challenging to increase model accuracy.
		- structured data are less likely to involve human labelers.

- # Labeling and Organizing data.
	- Obtaining dats :
		- get into iteration loop as quick as possible. if not start with a small data
		- ![[Pasted image 20220801191453.png]]
		- dimensions to keep in mind while collection data 
			1. amount of data .
			2. cost of collecting data.
			3. time required to collect that data.
			4. others -> like privacy,  quality and regulatory constrains
		- labeling data
			- inhouse or outsourced or crowdsourced (options)
			- MLE can do it for few days.
			- who is qualified to label.
	- # Data  pipelining
		- data manipulation happens to be very complex with dependencies of steps to its previous step.
		- Data provenance : from where the data came.
		- Data lineage : the very steps in the pipeline.
		- Meta Data : Data about data. 
		- two phase 
			- POC :
				- check if its worth it
				- focus on getting the prototype work
				- its ok if data pre processing is manual. BUT MSKE NOTE OF IT.
			- Production phase:
				- this is when those notes can be used to tune the much sophisticated tools to make sure the data pipeline is replicable.
	- Balanced train/dev/test split
		- keep in mind that distribution of classes when distributing when dataset is SMALL.
- Scoping
	- feasibility for the project 
	- scoping process:
		- brainstorm business problems-> brainstorm AI solutions ->check feasibility in terms of resource
	- ![[Pasted image 20220813144649.png]]
	- datagenerating link : [[ImageDatagenerator]]