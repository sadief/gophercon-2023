## Scaling Coffee with Goroutines

We'll walk through together from step 1 how to spin up a small web app and use Goroutines to take advantage of Go's impressive concurrency. By the end you'll be comfortable with:

- Using goroutines to run multiple functions at the same time
- Using wait groups to ensure goroutines have finished
- Running goroutines within goroutines for even better performance
- Basic Docker deployment

**Note:** There are additional modules to this tutorial on GitHub that required having Go, Docker, Kubernetes, and Minikube installed. This is if you would like to explore the kubernetes deployment and scaling portion, but may require some pre-existing kubernetes experience.

Feel free to follow along the instructions there instead if you would like to run this locally. [Here](https://github.com/sadief/gophercon-2023-slides-code) is the link to the repo