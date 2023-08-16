# Scale up the pods

**Task:** Scale up the pods

> Create an ingress file to manage the network traffic:

`touch ingress.yaml`{{copy}}

```
apiVersion: networking.k8s.io/v1
kind: Ingress

metadata:
  namespace: default
  name: coffee-shop
  labels:
    ingress-controller: nginx
  annotations:
    kubernetes.io/ingress.class: "nginx" 

spec:
  rules:
  - host: "localhost"
    http:
      paths:
      - pathType: Prefix
        path: "/"
        backend:
          service:
            name: coffee-shop
            port:
              number: 80
```{{copy}}

> Add the Service deployment instructions to the deployment.yaml

```
---
apiVersion: v1
kind: Service
metadata:
  name: coffee-shop
  labels:
    run: coffee-shop
spec:
  ports:
  - port: 80
    protocol: TCP
    targetPort: 8080
  selector:
    run: coffee-shop
  type: NodePort
  sessionAffinity: None
  ```{{copy}}

  > Add the ingress deployment to the Makefile `deploy` instructions

  ```
  deploy:	
	kubectl apply -f deployment.yaml
	kubectl apply -f ingress.yaml
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