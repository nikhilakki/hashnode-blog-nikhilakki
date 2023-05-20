---
title: "What are Channels?"
datePublished: Sat May 20 2023 16:45:39 GMT+0000 (Coordinated Universal Time)
cuid: clhw80tzq02h8b2nvf3os3rj4
slug: what-are-channels
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681662885649/2652b9a0-617f-466e-aa54-3382119d1728.png
tags: python, queue, threads, channels, rust-lang

---

Channels are commonly used in concurrent programming to communicate between threads or processes. They provide a way for different threads or processes to exchange data in a safe and synchronized manner.

### In simple words -

Channels are like a secret tunnel that connects two rooms. Imagine you and your friend are in separate rooms and want to pass notes to each other without anyone else seeing. You could use a secret tunnel, like a paper tube, to pass notes back and forth.

In programming, channels are like that secret tunnel, but instead of passing notes, we use them to send messages between different parts of a computer program. Just like the paper tube, the messages are hidden from everyone else except the sender and the receiver.

For example, imagine you have a game where one part of the program is responsible for updating the player's score, and another part is responsible for displaying it on the screen. They need to communicate with each other to make sure the score is updated and displayed correctly. They could use a channel to send messages back and forth, like passing notes through the secret tunnel.

Channels make it easy for different parts of a program to talk to each other without getting in each other's way. They're a powerful tool for building complex programs that work together seamlessly.

### Use-cases

Channels are useful in a variety of scenarios, including:

1. **Coordination between threads:** Channels can be used to synchronize the execution of different threads. For example, a producer thread could use a channel to send data to a consumer thread, allowing the consumer to block until new data is available.
    
2. **Load balancing:** Channels can be used to distribute work among a pool of worker threads. For example, a server could use a channel to receive incoming requests and then distribute them to a pool of worker threads.
    
3. **Event handling:** Channels can be used to notify one thread of an event that occurred in another thread. For example, a user interface thread could use a channel to notify a background thread that the user has clicked a button.
    
4. **Streaming data:** Channels can be used to stream data between threads or processes. For example, a video decoding application could use a channel to stream frames from a file reader thread to a rendering thread.
    

Overall, channels provide a powerful mechanism for communication and synchronization in concurrent programming, and are a core building block in many multi-threaded applications.

### Examples

Now here's a short example of channels in Python using the `threading and queue` module:

```python
import threading
import queue

def producer(q):
    for i in range(100):
        q.put(i*i)

def consumer(q):
    while True:
        item = q.get()
        if item is None:
            break
        print("Received:", item)

# Create a shared Queue
q = queue.Queue()

# Start a producer thread
threading.Thread(target=producer, args=(q,)).start()

# Start a consumer thread
threading.Thread(target=consumer, args=(q,)).start()

# Wait for the producer to finish
q.put(None)
```

Now here's a short example of channels in Rust using the `std::sync::mpsc` module:

```rust
use std::sync::mpsc;
use std::thread;

fn main() {
    // Initialize sender and receiver for i32
    let (sender, receiver) = mpsc::channel::<i32>();

    // Spawn a thread & move to send i32 data
    thread::spawn(move || {
        for i in 0..100 {
            sender.send(i*i).unwrap();
        }
    });

    // Receive in current thread
    for received in receiver {
        println!("Received: {}", received);
    }
}
```

*In both example, we create a channel with a capacity of 100 messages using* `queue.Queue()` *and* `mpsc::channel()`*. We then spawn a new thread that sends 100 integers through the channel using* `q.put(i)` *and* `sender.send(i)`*. Finally, we use a* `while` *&* `for` *loop to receive the messages from the channel using the* `receiver` *object, printing each received message to the console.*

### Resources

Here are some resources you can use to learn more about channels:

1. Rust Book: The Rust Programming Language book is a great resource for learning about Rust in general, and has a section specifically on channels. The book is available online for free at [https://doc.rust-lang.org/book/ch16-00-concurrency.html](https://doc.rust-lang.org/book/ch16-00-concurrency.html).
    
2. Rust By Example: The Rust By Example website has a section on channels that provides a variety of examples of how to use them. The site is available at [https://doc.rust-lang.org/stable/rust-by-example/std\_misc/channels.html](https://doc.rust-lang.org/stable/rust-by-example/std_misc/channels.html).
    
3. Rust documentation: The Rust standard library documentation includes detailed information about the `std::sync::mpsc` module, which provides the implementation for Rust's channels. You can find the documentation at [https://doc.rust-lang.org/std/sync/mpsc/](https://doc.rust-lang.org/std/sync/mpsc/).
    
4. Python documentation: If you're interested in learning about Python's queues, the official Python documentation is a good place to start. The `queue` module documentation is available at [https://docs.python.org/3/library/queue.html](https://docs.python.org/3/library/queue.html).
    
5. The Little Book of Rust Macros: This free e-book includes a chapter on channels and provides a detailed explanation of how to use them. You can download the book at [https://danielkeep.github.io/tlborm/book/README.html](https://danielkeep.github.io/tlborm/book/README.html).
    

I hope these resources help you learn more about channels and their use in Rust and Python!