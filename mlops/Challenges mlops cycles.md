- Concept drift and data drift
	- Gradual change
	- sudden shock - like the changes due to covid effect.
	- Concept drift -> mapping from x->y changes
	- Data drift -> change in the distribution of x.

- Software engineering issue.
	- Realtime or Batch work.
	- cloud vs edge/Browser.
	- Compute resources.
	- latency, throughput (QPS) queries per second.
	- logging.
	- security and privacy.

### common deployment cases 
 1. New product
 2. Automate
 3. Replace previous ML system.
- key ideas :
	- gradual ramp up
	- Rollback
- ## shadow mode: 
	- ML system shadows the human and runs in parallel but no decisions are made.
- ### Canary deployment: 
	- roll out to small fraction of traffic initially
- ## Blue green deployment:
	- switch between old (blue)version.'

## Degree of automation
```
	human-> shadow mode-> ai assitance-> partial automation-> full automation
```

	- depending on use case intervention of human decreases from left to right

- # Monitoring system:
	- dashboard : server load, fraction of non-null outputs, fraction of missing input values.
	- software metrics : memory, latency, throughput, server load.
	- input metrics: Avg input length, Avg input volume, num of missing values, avg img brightness
	- output metrics: times return "null", times user redoes search, times user switches over to alternative method(got frustrated by using the ml system), CTR(click through rate)
	- keep looking for the metrics which change and which don't.
	- set thresholds for alarms.
	- have ml pipeline monitoring.