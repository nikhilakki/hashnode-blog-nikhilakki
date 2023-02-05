# Series | Web frameworks in Python - FastAPI

Here are some of the main features of FastAPI, along with examples of how they can be used:

1. **Fast:** FastAPI is built on top of Starlette for high performance, with an easy-to-use interface for defining API endpoints.
    

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"Hello": "World"}
```

1. **Easy to use:** FastAPI provides an easy-to-use interface for defining API endpoints, with support for path and query parameters, request bodies, and more.
    

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/items/{item_id}")
def read_item(item_id: int, q: str = None):
    return {"item_id": item_id, "q": q}
```

1. **Dependency Injection**: FastAPI uses Pydantic models and dependency injection for request data validation and for injecting dependencies.
    

```python
from fastapi import FastAPI, Depends
from pydantic import BaseModel

class Item(BaseModel):
    name: str
    description: str = None
    price: float
    tax: float = None

app = FastAPI()

def validate_item(item: Item):
    if item.tax is None:
        item.tax = item.price * 0.1
    return item

@app.post("/items/")
def create_item(item: Item = Depends(validate_item)):
    return item
```

1. **FastAPI supports Asynchronous Programming**: FastAPI supports asynchronous programming, which allows you to take full advantage of the capabilities of your hardware.
    

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/users/")
async def read_users():
    return await fetch_users_from_database()
```

1. **Automatic generation of an OpenAPI schema**: FastAPI uses the Pydantic models to automatically generate an OpenAPI schema for your API. You can use this schema to automatically generate client libraries for your API.
    

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/items/{item_id}")
def read_item(item_id: int):
    return {"item_id": item_id}
```

These are just a few examples of the features of FastAPI. There are many other features available as well, such as support for authentication and authorization, built-in support for WebSockets, and more.

Here is an example of how you might use FastAPI to create a simple API endpoint:

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"Hello": "World"}

@app.get("/items/{item_id}")
def read_item(item_id: int, q: str = None):
    return {"item_id": item_id, "q": q}
```

The `FastAPI` class is the main entry point of the framework. An instance of this class is created and is passed to functions decorated with `app.route` as the first argument. The `@app.route` decorator creates an endpoint for your application. The first endpoint is a simple "Hello World" greeting, accessible at the "/" path. The second endpoint is for retrieving an item by ID, and takes an optional query parameter `q`.

### Uvicorn; a ASGI web server

**Uvicorn** is a high-performance web server that is often used to run FastAPI applications in production. It is built on top of the asyncio library, which allows it to handle a large number of concurrent connections efficiently.

One of the key features of Uvicorn is its built-in support for the ASGI (Asynchronous Server Gateway Interface) specification. This allows Uvicorn to work seamlessly with a wide variety of web frameworks, including FastAPI.

Here's an example of how you might use Uvicorn to run a FastAPI application:

```python
if __name__ == '__main__':
    import uvicorn
    uvicorn.run(app, host="127.0.0.1", port=8000)
```

*You can access the endpoints via browser by visiting* [`http://127.0.0.1:8000/`](http://127.0.0.1:8000/) *and* [`http://127.0.0.1:8000/items/42?q=test`](http://127.0.0.1:8000/items/42?q=test)

In this example, the [`uvicorn.run`](http://uvicorn.run)`()` function is used to start the Uvicorn server, passing in the FastAPI app as the first argument. The `host` and `port` arguments are used to configure the server to listen on all available network interfaces (`0.0.0.0`) on port 8000.

You can also configure uvicorn to run as a daemon, logging, workers and other options with uvicorn command.

```bash
uvicorn main:app --workers 4 --host 0.0.0.0 --port 8000
```

Uvicorn is known for its high performance and can handle a large number of concurrent connections, which makes it well-suited for running production-grade applications. Also, it has built-in support for ASGI, it can be used with other frameworks like Starlette, Django Channels, etc.

It's worth mentioning that you could use other servers like Gunicorn as well with FastAPI, but Uvicorn is specially designed for running async web applications, so it's been widely adopted for running a fastapi application.

### Closing thoughts -

FastAPI is my go-to framework for building a web / RESTfUL API server; be it a backend for web & mobile apps or hosting ML models on the cloud, FastAPI is a simple yet powerful tool to build for such use cases.