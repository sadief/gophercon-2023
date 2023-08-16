# 9. Bump up Resources

**Task:** Increase the cpu/memory resource so you can keep stress testing the pods

```        resources:
          limits:
            cpu: 4
            memory: 3092M
          requests:
            cpu: 2
            memory: 1024M
```{{copy}}

Deploy to Kubernetes again:

`make deploy`{{exec}}

>Here's a reminder of some of the handy commands:

`make deploy`{{exec}} from folder root to deploy image on k8's (remember to `make down` first if you haven't already so it tears down the old container)

`kubectl get pods`{{exec}} to see the coffee-shop pod running and grab the name of the pods

`kubectl describe pod <PODNAME>` for more info (helpful for debugging!)

`make forward`{{exec}} to port forward so you can run the endpoint

`curl http://localhost:8080/serve-customer/3`{{exec}} to hit endpoint on deployment

`kubectl logs <PODNAME>`{{exec}} to see your logs

`make down` to tear down deployment, stop container, and remove image