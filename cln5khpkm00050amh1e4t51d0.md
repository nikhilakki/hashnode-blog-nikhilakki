---
title: "Python Logging: Debugging with Style"
datePublished: Sat Sep 30 2023 05:03:09 GMT+0000 (Coordinated Universal Time)
cuid: cln5khpkm00050amh1e4t51d0
slug: python-logging-debugging-with-style
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695576490170/5c8ee5fd-b11a-478d-a51c-bca8b28871aa.png
tags: app-development, python, logging, python-logging

---

### Introduction

Logging is an essential aspect of Python development. It allows you to record important information, errors, and messages from your application, making it easier to troubleshoot issues and monitor its behaviour.

### Basic Logging Setup

In Python, you can set up logging using the built-in `logging` module. Here are the fundamental steps:

```python
import logging

# Configure logging
logging.basicConfig(
    level=logging.DEBUG,  # Set the desired logging level (DEBUG, INFO, WARNING, ERROR, CRITICAL)
    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
    handlers=[
        logging.FileHandler('app.log'),  # Save log messages to a file
        logging.StreamHandler()  # Display log messages in the console
    ]
)
# Create a logger
logger = logging.getLogger(__name__)
# Example usage
logger.debug('This is a debug message')
logger.info('This is an info message')
logger.warning('This is a warning message')
logger.error('This is an error message')
logger.critical('This is a critical message')
```

### Logging Levels

Python's `logging` module provides different log levels to categorize your messages:

* `DEBUG`: Detailed information for debugging.
    
* `INFO`: General information about the application's operations.
    
* `WARNING`: Indicating something unexpected, but not an error.
    
* `ERROR`: A genuine error that needs attention.
    
* `CRITICAL`: A critical error that may lead to the application's termination.
    

You can set the logging level to control which messages get recorded.

### Logging to Files

By using `logging.FileHandler`, you can save log messages to a file. This is useful for long-running applications and for historical analysis.

### Logging to Console

Using `logging.StreamHandler`, you can also display log messages in the console, which is helpful for real-time debugging.

### Logging Best Practices

* Use different loggers for different parts of your application.
    
* Consider rotating log files to prevent them from growing indefinitely.
    
* Avoid using `print()` for debugging; use appropriate log levels instead.
    
* Customize log formats to include timestamps, source information, etc.
    
* In production, configure logging to send logs to a central server for monitoring.
    

**Further Reading**

1. [Python Logging Documentation](https://docs.python.org/3/library/logging.html)
    
2. [A Comprehensive Guide to Python Logging](https://realpython.com/python-logging/) *(this best usage guide on this topic on the internet; a personal opinion)*
    
3. [Logging Best Practices in Python](https://www.toptal.com/python/in-depth-python-logging)
    
4. [Loguru](https://github.com/Delgan/loguru): An alternative logging library with a simpler syntax.
    

### Conclusion

Effective logging is an essential skill for every Python developer. By following these steps and best practices, you can set up logging in your Python applications to improve their maintainability and reliability.