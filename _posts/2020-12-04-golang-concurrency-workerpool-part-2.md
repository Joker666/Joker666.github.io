---
layout: post
category: example
---

![logo](https://hackernoon.com/images/3Ur17PtJhkV5UkAAJFu6z8t0fKg1-cz631ep.jpeg)

**Project Link: https://github.com/Joker666/goworkerpool**

Goroutines and channels are powerful language structs that make golang a powerful concurrent language. In the first part of the article, we explored, how we can build a workerpool to optimize the performance of the concurrency structs of golang namely limiting the resource utilization. But it was a simple example to demonstrate how we can go about it.

Here, we will build a robust solution according to the learning from the first part so that we can use this solution in any application. There are some solutions on the internet with complex architecture using dispatchers and all. In reality, we do not need it, we can do everything using one shared channel. Let's see how we can build that here

## Architecture

Here we make a generic workerpool package that can handle tasks with workers based on the desired concurrency. Let's see the directory structure.

```
workerpool
├── pool.go
├── task.go
└── worker.go
```

The `workerpool` directory is in the root folder of the project. Let's go over what `Task` is. `Task` is a single unit of work that needs to be processed. `Worker` is a simple worker function that handles running the task. And `Pool` actually handles the creation and managing the workers.

## Implementation

Let's code out `Task` first.