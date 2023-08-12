# 6. Deploy the program to kubernetes

**Task:** Set up a deployment file so we can deploy the Coffee program

> Create a new deployment file `touch deployment.yaml`

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
        image: coffee-shop
        imagePullPolicy: Never
```{{copy}}

> Add some new commands to the Makefile so we can easily deploy

```
deploy:	
	kubectl apply -f deployment.yaml

delete-deployment:
	kubectl delete -f deployment.yaml

up: run deploy

forward:
	kubectl port-forward deployment/coffee-shop 8080:8080

down: stop delete-deployment
```{{copy}}

> Boot up the deployment 

`make up` from folder root to build docker image, run container, and deploy on k8's
`make forward` to port forward so you can run the endpoint
`curl http://localhost:8080/serve-customer/3` to hit endpoint on deployment
`make down` to tear down deployment, stop container, and remove image