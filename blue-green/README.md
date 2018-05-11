This chart is to demonstrate use of Blue/Green deployment strategy.
It uses following primary resources:
1. service-prod: Serves the production traffic.
2. service-stage: Uased for test traffic.
3. Ingress: NGINX ingress controller - Based on HostName routes production traffic to service-prod, and test traffic to service-stage.
4. service-lb: loadbalances traffic from outside to Ingress.
5. Deployments [Simple NGINX Server]
    5.1 deployment-blue: 
    5.2 deployment-green:
    Both deployment yamls are identical : except for they target different slots[blue or green]. Which one to deploy is controlled by variables blue.enabled & green.enabled.

A key variable is productionSlot. Based on its value prod service is configured to route the traffic to that slot.
Following image is for the case when `productionSlot: blue`
![](initialstate.png)