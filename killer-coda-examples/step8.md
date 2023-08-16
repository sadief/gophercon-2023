# 8. Add Kubernetes resource limits

**Task:** Set resource limits for the pod

> Add these resource limits to the `deployment.yaml` at the bottom of the file

```
        resources:
          limits:
            cpu: 1m
            memory: 10Mi
          requests:
            cpu: 1m
            memory: 10Mi
```{{copy}}

Deploy to Kubernetes again:

`make deploy`{{exec}}

> Play around with this! Let out your inner chaos demon. Here's a reminder of some of the handy commands:

`make deploy`{{exec}} from folder root to deploy image on k8's (remember to `make down` first if you haven't already so it tears down the old container)

`kubectl get pods`{{exec}} to see the coffee-shop pod running and grab the name of the pods

`kubectl describe pod <PODNAME>` for more info (helpful for debugging!)

`make forward`{{exec}} to port forward so you can run the endpoint

`curl http://localhost:8080/serve-customer/3`{{exec}} to hit endpoint on deployment

`kubectl logs <PODNAME>`{{exec}} to see your logs

`make down` to tear down deployment, stop container, and remove image