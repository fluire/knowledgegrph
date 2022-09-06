[[statistics]]
- mr gossett grest work , must read the cult statistical significance
- t- distribution:
	- describes the mean of the sample.
	- it resembles the normal distribution for fairly large size of data.
	- as the degree of freedom increase t - distribution becomes the normal distribution.
	- it is meant for testing statistical significance eg: is the difference of evolution score between male and female significant.
	- few assumption:
		1. measuring scale follow continuous ordinal scale 
		2.  simple random samples.
		3. Bell - shape distribution
		4. Homogeneity of variance. for preventing any bias in data.
	- state you hypothesis;
		- Null hypothesis: µ1 = µ2
		- alternative hypothesis
		- set significance level: α = 0.05
	- use scipy.stat : it will return t statistics and p -value.
	- if p - value less the α reject null hypothesis.
- use Standard normal table to find the less than probabilities:
	- ![[Pasted image 20220610175717.png]]
	- go to row -> first digit and first digit after decimal of z-vzlue.
	- go to column -> second digit after decimal
	- or directly use the online converter.

Using the two-tailed test from a normal distribution:
- A professional basketball team wants to compare its performance with that of players in a regional league.
• The pros are known to have a historic mean of 12 points per game with a standard deviation of 5.5.
• A group of 36 regional players recorded on average 10.7 points per game.
• The pro coach would like to know whether his professional team scores on average are different from that of the regional players.
State the null hypothesis
• H_0x=p_1 ("The mean point of the regional players is not different from the historic mean")
• H_1:x #p_1 ("The mean point of the regional players is different from the historic mean")
When the population standard deviation is given and we are asked to deal with a sub-sample, the size (n) of the sub-sample is used in the
- ![[Pasted image 20220610205349.png]]