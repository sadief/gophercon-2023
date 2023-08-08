# Making Coffee without using concurrency
Create a new folder for the project and add the code to create the coffee in three separate actions (functions!)

`pwd cd goroutines`

`touch main.go`

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
```

Execute the program and see what happens

`go run main.go`