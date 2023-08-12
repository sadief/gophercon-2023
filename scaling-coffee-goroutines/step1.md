# 1. Making Coffee without using concurrency

**Task:** Write a program that prints out a log for each coffee action:
- Paying for the coffee
- Making the espresso
- Steaming the milk

Give each a two second delay and have them run one after the other.


**Steps**

> Create a new folder for the project and add the code to create the coffee in three separate actions (functions!)

`mkdir goroutines && cd goroutines && touch main.go`{{exec}}

> Navigate to the main.go file in the Editor tab and add the starter program code:

```
package main

import (
	"log"
	"time"
)

func main() {
	start := time.Now()
	PayForCoffee()
	MakeEspresso()
	SteamMilk()
	log.Printf("Coffee made, 1 customer served")

	timeTaken := time.Since(start)
	log.Printf("Took %s to serve coffee", timeTaken)
}
```{{copy}}

> Add the functions in (feel free to write your own or customize this however you see fit)

```
func PayForCoffee() {
	time.Sleep(2 * time.Second)
	log.Printf("Coffee paid for 💰")
}

func MakeEspresso() {
	time.Sleep(2 * time.Second)
	log.Printf("Espresso made ☕️")
}

func SteamMilk() {
	time.Sleep(2 * time.Second)
	log.Printf("Milk steamed 🥛")
}
```{{copy}}

> Execute the program and see what happens

`cd goroutines && go run main.go`{{exec}}