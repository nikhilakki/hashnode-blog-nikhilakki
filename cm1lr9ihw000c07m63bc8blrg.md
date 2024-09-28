---
title: "elixir 101"
datePublished: Sat Sep 28 2024 06:12:55 GMT+0000 (Coordinated Universal Time)
cuid: cm1lr9ihw000c07m63bc8blrg
slug: elixir-101
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1725424628310/e930b1c4-e9db-431d-9048-edfadb135096.png
tags: phoenix, erlang, concurrency, elixir, functional-programming, otp

---

Elixir is a functional, concurrent language built on the Erlang VM (BEAM), known for its fault tolerance and scalability. To get started you'll need to understand basic syntax, concurrency, pattern matching, and working with data structures.

#### 1\. **Basic Syntax**

* **Variables and Immutability**: Variables are immutable. Once you bind a value to a variable, it cannot be changed.
    

```elixir
x = 5
# x = 6  (will not work)
```

* **Atoms**: Constants whose name is their value, often used as labels or keys.
    

```elixir
:ok
:error
```

* **Tuples**: Fixed-size collections of values.
    

```elixir
{:ok, "Success"}
{:error, "Something went wrong"}
```

* **Lists**: Linked lists, frequently used for collections of data.
    

```elixir
[1, 2, 3, 4]
```

* **Maps**: Key-value stores for more complex data.
    

```elixir
%{name: "John", age: 30}
```

#### 2\. **Pattern Matching**

* Fundamental to Elixir, it’s used to de-structure data and bind variables.
    

```elixir
{:ok, result} = {:ok, 42}
```

#### 3\. **Control Flow**

* `case`: Used for branching logic based on pattern matching.
    

```elixir
case x do
  1 -> "one"
  2 -> "two"
  _ -> "something else"
end
```

* `cond`: Similar to `else if` in other languages.
    

```elixir
cond do
  x == 1 -> "one"
  x == 2 -> "two"
  true -> "something else"
end
```

* `with`: Chains pattern matching expressions, simplifying nested `case` statements.
    

```elixir
with {:ok, result} <- some_function(),
     {:ok, processed} <- another_function(result) do
  {:ok, processed}
else
  _ -> {:error, "Something went wrong"}
end
```

#### 4\. **Functions**

* Functions are first-class citizens and can be defined with multiple clauses using pattern matching.
    

```elixir
defmodule Math do
  def sum(a, b), do: a + b
  def factorial(0), do: 1
  def factorial(n), do: n * factorial(n - 1)
end
```

#### 5\. **Concurrency (Processes)**

* **Processes**: Lightweight and isolated. Use `spawn` to create a new process.
    

```elixir
spawn(fn -> IO.puts("Hello from another process") end)
```

* **Messaging**: Processes communicate via message passing.
    

```elixir
send(self(), {:hello, "world"})
receive do
  {:hello, msg} -> IO.puts(msg)
end
```

#### 6\. **Collections**

* **Enum Module**: Provides a set of algorithms for working with collections.
    

```elixir
Enum.map([1, 2, 3], fn x -> x * 2 end)
Enum.filter([1, 2, 3, 4], fn x -> rem(x, 2) == 0 end)
```

#### 7\. **Mix (Build Tool)**

* Elixir projects are managed with `mix`.
    

```bash
mix new my_project
cd my_project
mix compile
```

#### 8\. **Testing**

* Elixir has built-in support for testing with `ExUnit`.
    

```elixir
defmodule MathTest do
  use ExUnit.Case
  test "sum/2 adds two numbers" do
    assert Math.sum(1, 2) == 3
  end
end
```

### **Advance topics**

1. **Advanced OTP (Open Telecom Platform)**
    
    * Supervisors, GenServer, GenStage, and more complex process management are key to building robust, fault-tolerant applications. These tools manage how processes are spawned, monitored, and restarted in case of failure.
        
2. **Metaprogramming**
    
    * Elixir allows you to write code that generates code, primarily through macros. This is useful for DSLs (Domain-Specific Languages) and compile-time optimizations but is often complex.
        
3. **Distributed Systems**
    
    * Elixir excels at building distributed systems. Understanding clustering, distributed databases (like Mnesia), and how to build scalable systems across nodes would fall into this category.
        
4. **NIFs (Native Implemented Functions)**
    
    * Integrating with C/C++ code for performance-critical tasks. This requires careful handling due to potential side effects.
        
5. **Complex Multi-Process Architectures**
    
    * Designing and implementing systems with complex inter-process communication, where you need to manage state and concurrency across many processes.
        

### Conclusion

The above concepts should help you build and maintain most Elixir applications, especially in web development, where tools like Phoenix leverage these concepts.

I recommend reading the official docs.

%[http://elixir-lang.org/] 

**Image attribution**

1. [Image #1](https://elixir-lang.org/)
    
2. [Image #2](https://www.freepik.com/free-vector/magic-potion-bottles-set_9175377.htm#fromView=search&page=1&position=3&uuid=1682a432-bb4d-40f1-8192-751e162bac7e)