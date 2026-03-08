---
{"dg-publish":true,"permalink":"/vertex-ai-endpoint/"}
---


Vertex AI endpoint
- scale horizontally by adding replicas when CPU utilization crosses a set threshold
- min 1 replica = service remains available during low traffic, while keeping costs down
- max replica 8 = handles peak demand
- **traffic splitting**
	- run A/B test in production without creating additional endpoints 
	- A/B with few infrastructure changes
	- reduce risk of affecting user experience during testing
	- if results positive = gradually ramp up percentage of user traffic to new model