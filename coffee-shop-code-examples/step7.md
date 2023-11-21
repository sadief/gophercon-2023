# 7. Deploy the program to kubernetes

**Task:** Set up a deployment file so we can deploy the Coffee program

> Create a new deployment file 

`touch deployment.yaml`{{exec}}

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: coffee-shop
  namespace: default
spec:
  replicas: 1
  selector:
    matchLabels:
      coffee-shop: web
  template:
    metadata:
      labels:
        coffee-shop: web
    spec:
      containers:
      - name: coffee-shop
        image: sadesf/killercodagoroutinetest:coffee-shop
        imagePullPolicy: Always
```{{copy}}

> Stop the Docker container because we are now using a prebuilt image
`make stop`{{exec}}

> Add some new commands to the Makefile so we can easily deploy

```
deploy:	
	kubectl apply -f deployment.yaml

delete-deployment:
	kubectl delete -f deployment.yaml

forward:
	kubectl port-forward deployment/coffee-shop 8080:8080

down: stop delete-deployment
```{{copy}}

> Boot up the deployment 

`make deploy`{{exec}} from folder root to deploy image on k8's (remember to `make down` first if you haven't already so it tears down the old container)

`kubectl get pods`{{exec}} to see the coffee-shop pod running and grab the name of the pods

`kubectl describe pod <PODNAME>` for more info (helpful for debugging!)

`make forward`{{exec}} to port forward so you can run the endpoint

`curl http://localhost:8080/serve-customer/3`{{exec}} to hit endpoint on deployment

`kubectl logs <PODNAME>`{{exec}} to see your logs

> Now have some fun increasing the amount of customers until you break the pod

`make down` to tear down deployment, stop container, and remove image