# Use a Waitgroup

**Task:** Use a WaitGroup so the function doesn't complete until each goroutine has finished

> Add the `sync` import

`"sync"`{{copy}}

> Initialize a WaitGroup instance

`wg := sync.WaitGroup{}`{{copy}}

> Inside the loop, before you call the goroutine, increment the waitgroup by 1

`wg.Add(1)`

> Add wg.Defer() to the MakeCoffee() function and take it in as a parameter

```
func MakeCoffee(wg *sync.WaitGroup) {
	defer wg.Done()
	PayForCoffee()
	MakeEspresso()
	SteamMilk()
}
```{{copy}}

> Update where we call MakeCoffee() to take in the waitgroup pointer

`go MakeCoffee(&wg)`

> Now run the program again and check the printouts

`go run main.go`{{exec}} from folder root
`curl http://localhost:8080/serve-customer/3`{{exec}} from new terminal window while server is running