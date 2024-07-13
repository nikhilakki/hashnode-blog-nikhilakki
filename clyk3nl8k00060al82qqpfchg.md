---
title: "Go with the Flow: Navigating HTTP Services with chi"
datePublished: Sat Jul 13 2024 12:25:08 GMT+0000 (Coordinated Universal Time)
cuid: clyk3nl8k00060al82qqpfchg
slug: go-with-the-flow-navigating-http-services-with-chi
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720873454191/31eb8a0c-4e03-4440-a6d8-b7f83025508c.png
tags: golang, chi, nethttp, http-router, golang-router, chilib

---

In Go (Golang), `chi` is a lightweight, idiomatic and composable router for building HTTP services. It's designed to offer the power and flexibility of the standard library `net/http` package while providing a clean API for building complex applications with less code and more clarity.

Here are some of the key features and benefits of using `chi`:

1. **Lightweight and Idiomatic**: `chi` is designed to be simple and straightforward, sticking closely to Go's standard library idioms. This makes it easy to learn and integrate into existing Go projects.
    
2. **Composability**: `chi` allows you to build middleware and routes in a highly composable way. You can define routes and middlewares in a tree-like structure, enabling modular and reusable code.
    
3. **Middleware Support**: `chi` supports middleware out-of-the-box, allowing you to add functionalities like logging, authentication, and request validation easily.
    
4. **Context Aware**: `chi` is built on top of Go's context package, enabling you to pass request-scoped values, deadlines, and cancellations across API boundaries and goroutines.
    
5. **Performance**: `chi` is designed with performance in mind, providing minimal overhead while offering powerful routing capabilities.
    

## Example Usage

Here's a basic example of how to use `chi` to set up a simple web server:

```go
package main

import (
    "net/http"
    "github.com/go-chi/chi/v5"
    "github.com/go-chi/chi/v5/middleware"
)

func main() {
    r := chi.NewRouter()

    // Use some middleware
    r.Use(middleware.Logger)
    r.Use(middleware.Recoverer)

    // Define routes
    r.Get("/", func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte("Welcome to the home page!"))
    })

    r.Get("/hello", func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte("Hello, World!"))
    })

    // Start the server
    http.ListenAndServe(":8080", r)
}
```

### Setting Up Middleware

Middleware in `chi` can be applied globally to all routes or locally to specific routes or groups of routes. Here's an example:

```go
// Applying middleware globally
r.Use(middleware.Logger)

// Applying middleware to specific routes
r.With(middleware.BasicAuth("myRealm", map[string]string{"user": "password"})).
    Get("/secure", func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte("This is a secure endpoint"))
    })
```

### Nested Routes and Groups

You can also create nested routes and groups for better organization:

```go
coder.Route("/admin", func(r chi.Router) {
    r.Use(AdminOnly) // Apply middleware specific to this group

    r.Get("/", func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte("Admin home"))
    })

    r.Get("/dashboard", func(w http.ResponseWriter, r *http.Request) {
        w.Write([]byte("Admin dashboard"))
    })
})
```

### URL Parameters

`chi` allows you to define routes with parameters:

```go
coder.Get("/user/{userID}", func(w http.ResponseWriter, r *http.Request) {
    userID := chi.URLParam(r, "userID")
    w.Write([]byte("User ID: " + userID))
})
```

### Handling Subroutes

Subroutes can be defined to handle nested routing structures:

```go
coder.Route("/api", func(r chi.Router) {
    r.Get("/users", listUsers)
    r.Get("/users/{userID}", getUser)
    r.Post("/users", createUser)
})
```

### Middleware Example

Here's an example of a custom middleware that logs the request duration:

```go
codefunc requestDurationLogger(next http.Handler) http.Handler {
    return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
        start := time.Now()
        next.ServeHTTP(w, r)
        duration := time.Since(start)
        log.Printf("Request %s took %v", r.URL.Path, duration)
    })
}
// Applying the custom middleware
r.Use(requestDurationLogger)
```

### **Take-away**

`chi` is a lightweight, idiomatic, and composable Go router for building HTTP services. It offers middleware support, context awareness, and high performance. Its simple API allows for modular and reusable code, making it a powerful choice for developing complex web applications efficiently.

**Image attribution**

[#1 link](https://www.freepik.com/free-photo/full-shot-women-practising-tai-chi-together_38170906.htm#fromView=search&page=1&position=0&uuid=e41de973-3f73-48ff-90a3-a8f662519741)