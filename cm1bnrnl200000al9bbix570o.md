---
title: "What is Actor Model?"
datePublished: Sat Sep 21 2024 04:37:21 GMT+0000 (Coordinated Universal Time)
cuid: cm1bnrnl200000al9bbix570o
slug: what-is-actor-model
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1725424064465/b3209df8-f8e4-41f9-bd38-d7cea2bf74e7.png
tags: erlang, concurrency, elixir, akka, actor-model

---

The **Actor Model** is a conceptual model for dealing with concurrent computation. It was introduced by Carl Hewitt in the 1970s and has become a foundational model for designing distributed systems, particularly those requiring high levels of concurrency and fault tolerance.

### Key Concepts of the Actor Model

1. **Actors**:
    
    * An actor is the fundamental unit of computation in the Actor Model.
        
    * Each actor is an independent, isolated entity that encapsulates state, behavior, and communication.
        
    * Actors do not share state directly with other actors, which helps avoid common issues like race conditions.
        
2. **Message Passing**:
    
    * Actors communicate with each other exclusively through **message passing**.
        
    * Messages are sent asynchronously, meaning that the sender does not wait for the receiver to process the message before continuing its own work.
        
    * Messages are delivered to the recipient actor's mailbox, where they are queued until the actor is ready to process them.
        
3. **Concurrency**:
    
    * Each actor processes one message at a time, making its state changes atomic from the perspective of other actors.
        
    * This approach naturally avoids many concurrency problems like deadlocks and race conditions because actors do not directly interact with each other’s state.
        
    * The Actor Model is inherently concurrent, with each actor operating independently.
        
4. **Behavior**:
    
    * When an actor receives a message, it can:
        
        1. **Change its state**: Actors can update their internal state based on the message received.
            
        2. **Send messages**: Actors can send messages to other actors, thereby influencing their behavior.
            
        3. **Create new actors**: An actor can spawn new actors to handle subtasks or additional responsibilities.
            
5. **Decoupling and Fault Tolerance**:
    
    * The Actor Model naturally promotes **decoupling** of components. Since actors only interact via messages, they can operate independently, making the system more modular.
        
    * **Fault tolerance** is often implemented by using supervisors (actors that monitor other actors). If an actor fails, the supervisor can restart it, isolate the error, or escalate the issue according to a predefined strategy.
        

### Real-World Implementations

Several programming languages and frameworks have adopted the Actor Model for building concurrent and distributed systems:

1. **Erlang**:
    
    * Erlang's entire concurrency model is based on the Actor Model. It uses lightweight processes (actors) that communicate via message passing.
        
    * Erlang’s OTP (Open Telecom Platform) framework provides tools for building fault-tolerant, scalable systems using the Actor Model.
        
2. **Elixir**:
    
    * Elixir, running on the BEAM virtual machine (the same as Erlang), also uses the Actor Model extensively.
        
    * The language inherits Erlang's powerful tools for building distributed and fault-tolerant systems.
        
3. **Akka (Scala/Java)**:
    
    * Akka is a toolkit and runtime for building concurrent, distributed, and fault-tolerant applications on the JVM.
        
    * It implements the Actor Model, allowing developers to create systems where actors communicate via message passing.
        
4. **Microsoft Orleans**:
    
    * Orleans is a framework that brings the Actor Model to the .NET platform.
        
    * It is designed for building cloud-native applications with a focus on scalability and distributed systems.
        

### Example: Simple Actor in Elixir

Here’s a basic example of an actor in Elixir:

```elixir
defmodule SimpleActor do
  use GenServer

  # Client API
  def start_link(initial_state) do
    GenServer.start_link(__MODULE__, initial_state, name: __MODULE__)
  end

  def send_message(msg) do
    GenServer.cast(__MODULE__, {:message, msg})
  end

  # Server Callbacks
  def init(initial_state) do
    {:ok, initial_state}
  end

  def handle_cast({:message, msg}, state) do
    IO.puts("Received message: #{msg}")
    {:noreply, state}
  end
end

# Usage
SimpleActor.start_link(%{})
SimpleActor.send_message("Hello, Actor!")
```

In this example:

* `SimpleActor` is an actor.
    
* It starts with an initial state.
    
* It can receive messages using the `handle_cast/2` function, which processes messages asynchronously.
    

### Advantages of the Actor Model

1. **Concurrency and Parallelism**:
    
    * The Actor Model naturally supports concurrent operations, making it easier to build systems that take advantage of multi-core processors.
        
2. **Scalability**:
    
    * Due to its decoupled nature, systems built with the Actor Model can scale horizontally by distributing actors across multiple nodes.
        
3. **Fault Tolerance**:
    
    * The model supports robust error handling strategies, making it suitable for building reliable systems that can recover from failures.
        
4. **Modularity**:
    
    * Each actor is an isolated unit of computation, which encourages modular design and easier reasoning about system behavior.
        

### Summary

The Actor Model is a powerful paradigm for building concurrent and distributed systems. By modeling each component as an actor that communicates via message passing, it simplifies the design of systems that require high concurrency, fault tolerance, and scalability. Languages and frameworks like Erlang, Elixir, Akka, and Orleans leverage the Actor Model to build robust, scalable systems, particularly in domains like telecommunications, real-time processing, and cloud services.

**Image attribution**

1. [Image #1](https://www.freepik.com/free-photo/young-beautiful-stylish-sexy-woman-cinema-backstage-holding-movie-clapper_13887245.htm#fromView=search&page=1&position=2&uuid=65b6578f-e7a6-4da4-a565-02ac10fe0f2d)
    
2. [Elixir logo](https://elixir-lang.org/)