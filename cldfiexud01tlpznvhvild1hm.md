# Intro to TOML configuration file format

### What is TOML?

TOML (Tom's Obvious, Minimal Language) is a file format used for configuration files. It is designed to be easy to read and write and is similar in structure to INI files.

The basic structure of a TOML file consists of key-value pairs, where keys are strings and values can be strings, numbers, booleans, or arrays of those types. Keys are separated from values by an equals sign (=) and keys are separated from one another by a newline.

One of the main advantages of TOML is its simplicity. It is easy to understand and work with, even for those who are not familiar with the format. Additionally, TOML supports comments and has a clear and consistent syntax, which makes it easy to write and maintain.

One of the main disadvantages of TOML is that it does not support all the features of more complex formats such as JSON or YAML. For example, TOML does not support nested data structures, and it can only represent a limited set of data types.

In summary, TOML is a simple and easy-to-read/write configuration file format that is great for small and medium-sized projects but may not be suitable for large, complex projects that require more advanced features.

### How does it compare with other formats?

Below is a comparison of TOML with some other popular configuration file formats:

* **JSON** is a widely used data interchange format that is often used for configuration files. It is more powerful than TOML, as it supports nested data structures and a wider range of data types. However, it is also more verbose and less human-readable than TOML.
    
* **YAML** is another popular configuration file format that is similar to TOML in terms of readability and simplicity. Like JSON, YAML supports nested data structures and a wide range of data types. However, it has a more complex syntax and is more prone to errors.
    
* **INI** is an older format that is similar to TOML in terms of structure, but it is less powerful and less flexible. It is mostly used for simple configuration files.
    
* **XML** is a markup language that is often used for configuration files, but it is more complex and verbose than TOML and other formats. It is not as human-readable as TOML and harder to parse.
    

### Why use TOML over YAML?

Both are popular configuration file formats that are designed to be easy to read and write. Here are a few benefits of using TOML over YAML:

* **Simplicity**: TOML has a simpler and more consistent syntax than YAML. This makes it easier for developers to understand and work with, especially for those who are not familiar with YAML.
    
* **Performance**: TOML is generally faster to parse and write than YAML. This can be important in situations where configuration files are read or written frequently.
    
* **Error-prone**: YAML's syntax is more complex, and it is more prone to errors. For example, indentation-based scoping in YAML can make it difficult to spot errors and can lead to unexpected results.
    
* **Human-readable**: TOML is designed to be more human-readable than YAML. Its syntax is closer to traditional configuration file formats such as INI, and it is less prone to errors caused by whitespace.
    
* **Comments**: TOML supports comments, which can be useful for documenting configuration files. YAML does not support comments natively, but they can be added with a specific syntax.
    

It's worth noting that YAML has its advantages over TOML, it supports nested data structures, and a wider range of data types. It's best to choose the format that best suits your needs and your team's skills.

### TOML File example

Here is an example of a simple TOML file:

```ini
title = "Sample TOML File"

[author]
name = "Nikhil Akki"
email = "akki@gopythonrust.com"

[database]
server = "localhost"
port = 5432
username = "root"
password = "super-secret"
```

You can write this kind of file in a text editor and save it with a .toml extension.

### TOML in Python

You can also programmatically read or write TOML files using a [library such as `toml`](https://github.com/uiri/toml) in python.

```python
import toml

with open("config.toml", "r") as f:
    config = toml.load(f)

print("Title:", config["title"])
print("Author:", config["author"]["name"])
print("Email:", config["author"]["email"])
```

In this example, we first open the file `config.toml` using the `open` function. Then, we use the `toml.load` function to parse the contents of the file into a dictionary object. Finally, we access the values of the config using the keys of the dictionary

*Python 3.11 has added read-only support for TOML files in the Python Standard library for more info check out the official* [*docs here*](https://docs.python.org/3/library/tomllib.html)*.*

%[https://docs.python.org/3/library/tomllib.html] 

### TOML in Golang

Here's an example of reading a TOML file in Go:

```go
package main

import (
    "fmt"
    "github.com/BurntSushi/toml"
)

type Config struct {
    Title  string
    Author struct {
        Name  string
        Email string
    }
}

func main() {
    var config Config
    _, err := toml.DecodeFile("config.toml", &config)
    if err != nil {
        panic(err)
    }
    fmt.Println("Title:", config.Title)
    fmt.Println("Author:", config.Author.Name)
    fmt.Println("Email:", config.Author.Email)
}
```

In this example, we first import the `fmt` and [`github.com/BurntSushi/toml`](http://github.com/BurntSushi/toml) packages. Next, we define a struct `Config` that corresponds to the structure of our TOML file. Then we use the `toml.DecodeFile` function to parse the contents of the file into a variable of the `Config` struct type. Finally, we access the values of the config using the struct fields, and print them out using the `fmt.Println` function.

You can see that it's much more readable and maintainable than the other examples, it's because structs provide a clear and organized way to represent the data, and the `DecodeFile` function does the heavy lifting of parsing the toml file.

Both examples demonstrate how to read TOML files, but the implementation is different. You can use the one that best suits your needs and your team's skills.

### Takeaway

Overall, TOML is a good choice for configuration files because of its simplicity and readability. JSON and YAML are more powerful and flexible, but they can be more difficult to work with. INI is simpler than TOML but less powerful, while XML is less human-readable and more complex.

### Source code

%[https://github.com/nikhilakki/toml-in-pyrsgo]