# Use a Waitgroup

**Task:** Use a WaitGroup so the function doesn't complete until each goroutine has finished

> Add the `sync` import

`"sync"`{{copy}}

> Initialize a WaitGroup instance

`wg := sync.WaitGroup{}`{{copy}}

> Inside the loop, before you call the goroutine, increment the waitgroup by 1

`wg.Add(1)`

> Now run the program again and check the printouts

`go run main.go`{{exec}} from folder root
`curl http://localhost:8080/serve-customer/3`{{exec}} from new terminal window while server is running