# 3. Use a Goroutine

**Task:** Use a Goroutine to have `MakeCoffee` run at the same time for each of the 3 customers

> Put `go` at the beginning of `MakeCoffee()`. It's that easy! (well, kinda)

`go MakeCoffee()`{{copy}}

> Try running the program again to see what happens

`go run main.go`{{exec}} from folder root
`curl http://localhost:8080/serve-customer/3`{{exec}} from new terminal window while server is running

The printout looks a bit sus doesn't it?
