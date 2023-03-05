---
title: "Series | Web frameworks in Python - Bottle"
seoTitle: "Web frameworks in Python - Bottle"
seoDescription: "Bottle, a micro-framework built with Python Standard Library and no additional dependency!"
datePublished: Sat Jan 07 2023 10:05:42 GMT+0000 (Coordinated Universal Time)
cuid: clcls67b00b3e8jnv9n3a6bh6
slug: series-web-frameworks-in-python-bottle
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1672810575118/0f60711d-f64f-4575-a2f1-8c67de005c72.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1672811220925/aaec5924-156e-4a5d-9f88-fc618bef736f.jpeg
tags: python, restful, webserver, microframework, python-bottle

---

**Bottle** is a lightweight web framework for Python. It is designed to be fast and easy to use, and it is well-suited for developing small to medium-sized web applications. Some of the key features of Bottle include:

* A built-in WSGI web server, which allows you to run your app without installing any additional libraries
    
* A simple templating system that allows you to easily generate HTML or other types of content
    
* A routing system that makes it easy to create URL patterns and bind them to your Python code
    
* A powerful plugin system that allows you to easily extend the functionality of your app
    

To use Bottle, you will need to have Python installed on your machine. Then, you can install Bottle using `pip`, the Python package manager. Once you have Bottle installed, you can create a simple web application by writing a few lines of Python code. For example, here's how you might create a "Hello, World!" app using Bottle:

```python
from bottle import Bottle, run

app = Bottle()

@app.route('/')
def hello():
    return "Hello, World!"

run(app, host='localhost', port=8080)
```

This code creates a new Bottle application, defines a route for the root URL (`/`), and then starts the web server. When you visit [`http://localhost:8080/`](http://localhost:8080/) in your web browser, you should see the message "Hello, World!" displayed.

**A more useful example -**

Now let's build a static file server using Bottle

```python
@app.route("/files/<filename:path>")
def serve_static(filename):
    return static_file(filename, root=PATH)
```

The above code defines a route that matches any URL. When a request is received, the `serve_static` function is called and the requested file is served from the directory `PATH` passed as arg `root`.

```python
@app.route("/")
def hello():
    files = os.listdir(PATH)
    return template(
        """
        <h2>Files in folder {{ PATH }}</h2>
        <p>
            <ol>
                % for file in files:
                <li> <a href=/files/{{ file }}>{{ file }}</a></li>
                % end
            </ol>
        </p>
    """,
        PATH=PATH,
        files=files,
    )
```

This section of the code defines a route that lists and displays the files in HTML format. The look is quite basic but we can extend the HTML template to look more beautiful by adding some CSS magic. We could even separate the template logic into an HTML file.

### Source Code -

%[https://github.com/nikhilakki/bottle-static-file-server] 

Let me know if you have any other questions about Bottle or web development in Python.