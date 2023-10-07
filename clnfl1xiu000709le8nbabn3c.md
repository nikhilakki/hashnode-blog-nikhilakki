---
title: "Loguru: Logging in Python Made Fun and Easy"
datePublished: Sat Oct 07 2023 05:16:34 GMT+0000 (Coordinated Universal Time)
cuid: clnfl1xiu000709le8nbabn3c
slug: loguru-logging-in-python-made-fun-and-easy
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695576650631/e2da3a29-1f2a-41ae-8396-dda87ffe2e85.png
tags: python3, python-logging, loguru, app-logging, backend-development-python

---

### Introduction

Loguru is a Python logging library that provides a simple and elegant way to configure and use logging. It offers powerful features while maintaining an easy-to-use interface.

### Installation

You can install Loguru using pip:

```bash
pip install loguru
```

### Basic Usage

Here's a basic example of how to use Loguru:

```python
from loguru import logger

# Configure Loguru
logger.add("app.log", rotation="500 MB", level="INFO")

# Log messages
logger.debug("This is a debug message")
logger.info("This is an info message")
logger.warning("This is a warning message")
logger.error("This is an error message")
logger.critical("This is a critical message")
```

Loguru automatically handles log rotation, which is very useful for managing log file sizes.

**Custom Formatting**

You can easily customize the log message format:

```python
from loguru import logger

logger.add("app.log", rotation="500 MB", level="INFO", format="{time:YYYY-MM-DD HH:mm:ss} | {level} | {message}")
logger.info("Customized log message format")
```

Loguru can log into the console as well:

```python
from loguru import logger

logger.add("app.log", rotation="500 MB", level="INFO", format="{time:YYYY-MM-DD HH:mm:ss} | {level} | {message}")
logger.add(sys.stdout, level="INFO")  # Log to console
logger.info("This message goes to both file and console")
```

**Exception Logging**

Loguru simplifies exception logging:

```python
try:
    # Code that may raise an exception
    result = 1 / 0
except Exception as e:
    logger.exception("An error occurred: {e}")
```

Loguru automatically includes the traceback in the log message.

### Why use Loguru over the std logging module?

Loguru is a Python logging library that offers several advantages over the standard `logging` module, making it a compelling choice for developers.

Here's a comparison of Loguru with the default `logging` module and why someone might choose it:

**1\. Simplicity and Readability:**

* **Loguru**: Loguru provides a simplified and intuitive syntax for configuring and using logging. Its API is designed to be straightforward, making it easier to set up and maintain.
    
* **logging**: The standard `logging` module in Python can be complex and verbose, requiring more lines of code to achieve the same logging functionality. It may lead to less readable code.
    

**2\. Custom Formatting:**

* **Loguru**: Loguru allows you to easily customize log message formatting using a flexible and concise format string. This simplifies the process of tailoring log messages to your specific needs.
    
* **logging**: Customizing log message formatting in the standard `logging` module can be more cumbersome and less intuitive.
    

**3\. Log Rotation:**

* **Loguru**: Loguru provides built-in log rotation with straightforward options, such as specifying log file sizes for rotation. This simplifies log file management.
    
* **logging**: Log rotation in the standard `logging` module often requires additional configuration and may be less intuitive.
    

**4\. Exception Handling:**

* **Loguru**: Loguru simplifies exception logging by providing a convenient `logger.exception()` method, which automatically includes the traceback in the log message.
    
* **logging**: In the standard `logging` module, including tracebacks in log messages typically requires more manual coding.
    

**5\. Colored Output:**

* **Loguru**: Loguru supports colored console output, making it easier to distinguish log levels in the console.
    
* **logging**: Achieving colored console output in the standard `logging` module may involve additional customization.
    

**6\. Integration with External Libraries:**

* **Loguru**: Loguru can be more straightforward to integrate with external libraries and frameworks due to its simplified API.
    
* **logging**: While the standard `logging` module is widely supported, it can sometimes require more effort to integrate with specific libraries.
    

**7\. Active Development:**

* **Loguru**: Loguru is actively maintained and updated, incorporating user feedback and improvements.
    
* **logging**: The standard `logging` module is a part of Python's standard library and may have a slower development cycle (*this could be a plus depending on your project requirements*).
    

**8\. Third-party Handlers:**

* **Loguru**: While Loguru provides essential functionality out of the box, it also supports third-party handlers and extensions for more advanced use cases.
    
* **logging**: The standard `logging` module has a wide range of handlers available, but using them may require more configuration and code.
    

### Conclusion

In summary, Loguru offers a more straightforward and user-friendly logging experience with a focus on simplicity and readability. Developers who prefer a clean and intuitive API, along with features like custom formatting, log rotation, and exception handling, may find Loguru to be a valuable alternative to the standard `logging` module.

### **Further Reading**

1. [**Loguru Documentation**](https://loguru.readthedocs.io/en/stable/index.html): The official documentation provides detailed information and advanced features.
    
2. [**Loguru GitHub Repository**](https://github.com/Delgan/loguru): You can find the source code and examples here.