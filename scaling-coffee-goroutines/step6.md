# 6. Run the program inside a Docker container

**Task:** Deploy the program inside a Docker container to prepare for using with Kubernetes

> Create a Dockerfile inside your folder

`touch Dockerfile`{{exec}}

> Add these commands to build and run the coffee program

```
FROM golang:1.18.4-alpine

WORKDIR /app

COPY go.mod ./
RUN go mod download

COPY *.go ./

RUN go build -o /coffee-shop

EXPOSE 8080

CMD [ "/coffee-shop" ]
```{{copy}}

> Create a Makefile for simpler commands

`touch Makefile`{{exec}}

> Add these commands to the Makefile to build, run, and stop the Docker container

```
build:
	docker build --tag coffee-shop .

run:	build
	docker run -d --name coffee-shop -p 8080:8080 coffee-shop

stop:	
	docker stop coffee-shop
	docker container rm coffee-shop
```{{copy}}

> Lastly, add a `go.mod` for dependency management

`touch go.mod`{{exec}}

> Add the following to the go.mod

```
module coffee-shop

go 1.18
```{{copy}}

> Try building the image and running the container

`make run`{{exec}} from folder root to build docker container
`curl http://localhost:8080/serve-customer/3`{{exec}} from new terminal window while container is running
`make stop`{{exec}} to stop container and remove image
`docker logs -f coffee-shop` to check the logs