# 2. Serve More Coffee

**Task:** Adapt the program to accept an HTTP request with a parameter for the number of customers:

eg. `curl http://localhost:8080/serve-customer/3`

Where `3` is the parameter.

**Steps**

> Adapt the main function to set up an http server using the Go `http` library

```
package main

import (
	"log"
	"net/http"
	"strconv"
	"strings"
	"time"
)

func main() {
	http.HandleFunc("/serve-customer/", ServeCustomer)
	http.ListenAndServe(":8080", nil)
}
```{{copy}}

> Write the `ServeCustomer` function that will be called from the http request.
This should loop through the number given as a parameter, and call the function to 'MakeCoffee'

```
func ServeCustomer(w http.ResponseWriter, r *http.Request) {
	start := time.Now()

	numCustomers, err := strconv.Atoi(strings.TrimPrefix(r.URL.Path, "/serve-customer/"))
	if err != nil || numCustomers == 0 {
		numCustomers = 1
	}

	count := 0
	for i := 0; i < numCustomers; i++ {
		MakeCoffee()
		count++
	}

	timeTaken := time.Since(start)
	log.Printf("Took %s to serve coffee to %v customer(s)", timeTaken, count)
}
```{{copy}}


> Group our three functions into one parent function for easier use

```
func MakeCoffee() {
	PayForCoffee()
	MakeEspresso()
	SteamMilk()
}
```{{copy}}

>  Try hitting the endpoint

`go run main.go`{{exec}} from folder root
`curl http://localhost:8080/serve-customer/3`{{exec}} from new terminal window while server is running

> You can `ctrl+c` to stop the program