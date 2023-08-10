# Making Coffee without using concurrency

**Task:** Write a program that prints out a log for each coffee action:
- Paying for the coffee
- Making the espresso
- Steaming the milk

Give each a two second delay and have them run one after the other.


**Steps**

1. Create a new folder for the project and add the code to create the coffee in three separate actions (functions!)

`mkdir goroutines && cd goroutines && touch main.go`{{exec}}

2. Navigate to the main.go file in the Editor tab and add the starter program code:
Hint: It'll be under `filesystem/root/goroutines`

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

3. Add the functions in (feel free to write your own or customize this however you see fit)

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

4. Execute the program and see what happens

`go run main.go`{{exec}}