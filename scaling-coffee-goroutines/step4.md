# 4. Use a Waitgroup

**Task:** Use a WaitGroup so the function doesn't complete until each goroutine has finished

> Add the `sync` import

`"sync"`{{copy}}

> Initialize a WaitGroup instance within `ServeCustomer` ust before the loop

`wg := sync.WaitGroup{}`{{copy}}

> Inside the loop, before you call the goroutine, increment the waitgroup by 1

`wg.Add(1)`{{copy}}

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

`go MakeCoffee(&wg)`{{copy}}

> Add the 'Wait' after the for loop so the function knows not to finish before the waitgroup has completed

`wg.Wait()`{{copy}}

> Now run the program again and check the printouts

`go run main.go`{{exec}} from folder root
`curl http://localhost:8080/serve-customer/3`{{exec}} from new terminal window while server is running

You should be back in the "6 seconds" running time now as these actions are happening in parallel