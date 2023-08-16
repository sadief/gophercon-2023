# 5. Add More Goroutines

**Task:** Add goroutines to the sub-functions to improve the speed of MakeCoffee()

> Turn the the sub-functions into goroutines by adding `go` and waitgroups

```
func MakeCoffee(wg *sync.WaitGroup) {
	defer wg.Done()

	newWg := sync.WaitGroup{}
	newWg.Add(3)
	go PayForCoffee(&newWg)
	go MakeEspresso(&newWg)
	go SteamMilk(&newWg)
	newWg.Wait()
}
```{{copy}}

> Adapt each function to take in the waitgroup and add a `defer`

```
func PayForCoffee(wg *sync.WaitGroup) {
	defer wg.Done()
	time.Sleep(2 * time.Second)
	log.Printf("Coffee paid for 💰")
}

func MakeEspresso(wg *sync.WaitGroup) {
	defer wg.Done()
	time.Sleep(2 * time.Second)
	log.Printf("Espresso made ☕️")
}

func SteamMilk(wg *sync.WaitGroup) {
	defer wg.Done()
	time.Sleep(2 * time.Second)
	log.Printf("Milk steamed 🥛")
}
```{{copy}}

> Now run the program again and check the printouts

`go run main.go`{{exec}} from folder root
`curl http://localhost:8080/serve-customer/3`{{exec}} from new terminal window while server is running

