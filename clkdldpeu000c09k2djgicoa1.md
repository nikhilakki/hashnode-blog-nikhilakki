---
title: "Understanding Method Chaining in Python"
datePublished: Sat Jul 22 2023 05:51:04 GMT+0000 (Coordinated Universal Time)
cuid: clkdldpeu000c09k2djgicoa1
slug: understanding-method-chaining-in-python
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688299244962/34ac6d37-46b7-4a7e-9723-05d4a1ff1ef7.png
tags: python, programming-tips, method-chaining, python-method-chaining, classes-python

---

### **Introduction**

Method chaining is a powerful programming pattern that allows you to call multiple methods on an object in a single line of code. It enhances code readability and conciseness by eliminating the need for intermediate variables or repeated method calls. In this blog post, we'll explore method chaining in Python, explain it using a simple example, discuss its use cases, and conclude with its benefits.

### **Simpler explanation**

Method chaining can be explained in simple terms as performing a series of operations on an object by chaining together multiple method calls. Each method modifies the object and returns the modified object itself. This pattern allows us to write cleaner and more readable code by combining multiple actions into a single line.

### **Example Code**

Let's understand method chaining through a practical example. Consider a class called `MethodChainingExample` with three methods: `add()`, `multiply()`, and `subtract()`. We'll implement method chaining by ensuring that each method returns the modified object. Take a look at the annotated code below:

```python
from typing import Self

class MethodChainingExample:
    def __init__(self) -> None:
        self.value = 0

    def add(self, num: int) -> Self:
        self.value += num
        return self

    def multiply(self, num: int) -> Self:
        self.value *= num
        return self

    def subtract(self, num: int) -> Self:
        self.value -= num
        return self

# Creating an instance of MethodChainingExample
method_chaining_example = MethodChainingExample()

# Method chaining example
result = method_chaining_example.add(5).multiply(3).subtract(2)

print(result.value)  # Output: 13
```

In the above code, we create an instance of the `MethodChainingExample` and then perform a series of operations using method chaining. The `add()` method adds a value to the object, the `multiply()` method multiplies the value, and the `subtract()` method subtracts a value. Each method modifies the object and returns it, allowing us to chain subsequent method calls. Finally, we print the resulting value, which is 13.

### **Use Cases of Method Chaining**

Method chaining finds applications in various scenarios, including:

1. **Data manipulation:** Method chaining is useful when performing operations on collections or data structures, such as filtering, mapping, and reducing data.
    
2. **Querying databases:** Method chaining is commonly used in query builders or Object Relational Mapping (ORM) libraries to construct complex database queries.
    
3. **Configuration settings:** Method chaining is employed to set various configuration options on an object, where each method call modifies a specific setting.
    
4. **Fluent APIs:** Method chaining allows for the creation of fluent APIs, where the chain of method calls reads like a sentence, providing an intuitive and expressive coding style.
    

### **Conclusion**

Method chaining is a powerful technique in Python that enables us to perform a sequence of operations on an object in a concise and readable manner. By returning the modified object from each method, we can chain multiple method calls together, making our code more expressive and efficient. Whether it's manipulating data, querying databases, configuring settings, or building fluent APIs, method chaining offers a clean and elegant solution. Start using method chaining in your Python projects and experience the benefits of this pattern firsthand.

In addition to Python, languages like JavaScript (with libraries like jQuery), Ruby (with ActiveRecord), and Kotlin also make frequent use of method chaining to improve code readability and conciseness.