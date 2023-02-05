# Using Make for dev workflow automation

### **Intro**

I used to use Python or (mostly) Bash scripts to configure command-line automation, writing Python scripts is a lot more powerful but it comes with a dependency i.e. the Python interpreter. This could be a problem in lean OSes in a Server, VM or Container setup where you only have barebones software, that comes out of the box like `sh` or `bash` along with a few good other UNIX utilities.

Writing bash scripts is challenging if you are new to the language and even experienced scripters need to refer to a cheatsheet while writing Bash scripts. In simple words, it ain't user-friendly or intuitive in my opinion.

### **What is the solution?**

`make` is a command-line tool that is typically used to automate build and compilation processes for software development. It uses a "**makefile**" that defines a set of rules for building the software.

To use `make` for automation, you will need to first create a makefile. A makefile typically includes the following:

* Targets: The names of the files or actions that you want to build or execute.
    
* Dependencies: The files that a target depends on.
    
* Recipes: The commands that are executed to build or execute a target.
    

### **How to use** `make`?

Here's an example makefile that shows how to use `make` to compile a Rust program:

```makefile
all: main.rs rustc main.rs
```

This makefile defines a target named "all" that depends on the file "[**main.rs**](http://main.rs)". The recipe for building this target is to run the command "rustc [**main.rs**](http://main.rs)", which will compile the program using the rust compiler.

To build the program, you would simply run the command "make" on the command line. This will execute the recipe for the "all" target and will create an executable file named "main" in the same directory as the source file.

You can also use `make` to perform other tasks like running tests, building documentation, or deploying the application.

To run tests you can add a new target called `test` that depends on the binary executable and calls the testing framework like this:

```makefile
test: all ./main --test
```

You can also add more targets and dependencies to the makefile as needed to automate your development process.

You can use `make` to automate your development process by defining targets for each of the tasks that you need to perform and then specifying the dependencies and recipes for each target in your makefile.

### **How to configure environment variables?**

You can pass environment variables to a command in a makefile recipe by prefixing the command with the `export` command. For example, if you want to pass an environment variable named `VAR` with the value `value` to a command, you can do it like this:

```makefile
all: export VAR=value; command
```

You can also use the `-e` flag with `make` command to export the variable before running the recipe:

```makefile
all: make -e VAR=value command
```

Alternatively, you can use the `ENV` variable:

```makefile
all: command ENV=VAR=value
```

You can also use variable references in the command:

```makefile
all: command --arg $(VAR)
```

It is also possible to pass environment variables to the `make` command when running it, like this:

```bash
VAR=value make
```

Keep in mind that environment variables set in this way will only be available within the context of the `make` command and any commands that it runs. If you need to set an environment variable for the entire shell session, you will need to do it in a separate step, outside of the makefile.

### **Takeaways**

**Make** is a great tool for automating your software development process, be it common dev commands for building, testing or compiling your source code.

We use it in our CI/CD automation workflows and also to automate and abstract some repeated commands for local development.

Hope you found this short article useful, spread the good word - like and share!