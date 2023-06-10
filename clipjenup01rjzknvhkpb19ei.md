---
title: "Python for web backend - Requests vs Urllib3"
datePublished: Sat Jun 10 2023 05:09:39 GMT+0000 (Coordinated Universal Time)
cuid: clipjenup01rjzknvhkpb19ei
slug: python-for-web-backend-requests-vs-urllib3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1683869593674/8707dcd4-5aa5-465c-80d9-e1fcbd39bc77.png
tags: http, python, http-requests, requests, urllib3

---

Both [Requests](https://github.com/psf/requests) and [urllib3](https://github.com/urllib3/urllib3) are Python libraries that provide easy-to-use interfaces for sending HTTP requests and handling responses. However, there are some differences between the two:

1. [**Requests**](https://requests.readthedocs.io/en/latest/) **is a higher-level library** that provides a more intuitive and Pythonic interface for sending HTTP requests. It abstracts away much of the low-level details of the HTTP protocol, making it easier to use for most common use cases. In contrast, urllib3 is a lower-level library that provides a more detailed API for handling HTTP requests and responses.
    
2. **Requests is built on top of urllib3**, so it includes urllib3's functionality and also extends it with additional features. This means that Requests can do everything that urllib3 can do, but Requests offers a simpler and more convenient API.
    
3. **Requests has built-in support for many features that urllib3 does not have**, such as authentication, cookie handling, and session management. Requests also has a more robust error handling system that provides more informative error messages.
    
4. [urllib3](https://urllib3.readthedocs.io/en/stable/user-guide.html) **is a standalone library**, so it can be used in any Python project without additional dependencies. In contrast, Requests has some dependencies, such as urllib3 and chardet.
    

### Requests like API implementation in Urllib3

Here's a custom wrapper over urllib3 that has a similar API to Requests:

```python
import urllib3

class CustomRequests:
    def __init__(self):
        self.session = urllib3.PoolManager()

    def get(self, url, **kwargs):
        response = self.session.request('GET', url, **kwargs)
        return CustomResponse(response)

    def post(self, url, data=None, json=None, **kwargs):
        if json:
            kwargs['body'] = json
            headers = kwargs.pop('headers', {})
            headers['Content-Type'] = 'application/json'
            kwargs['headers'] = headers
        elif data:
            kwargs['body'] = data
        response = self.session.request('POST', url, **kwargs)
        return CustomResponse(response)

    # Add more methods as needed

class CustomResponse:
    def __init__(self, response):
        self.response = response

    @property
    def content(self):
        return self.response.data

    @property
    def text(self):
        return self.response.data.decode('utf-8')

    @property
    def status_code(self):
        return self.response.status

    # Add more properties and methods as needed
```

In this example, `CustomRequests` is a custom wrapper class that has `get` and `post` methods that are similar to Requests' methods. `CustomResponse` is a custom response class that has properties and methods that are similar to Requests' response class.

You can use this custom wrapper class in the same way you would use Requests:

```python
custom_requests = CustomRequests()
response = custom_requests.get('https://www.example.com')
print(response.text)
```

Note that this is a simplified implementation and may not handle all the edge cases that Requests handles. You may need to add more features or methods to the custom wrapper class to handle all your use cases. And for a slightly more ellaborate implementation go to the **Source code section** at the bottom.

### Why choose Urllib3 over Requests?

Both urllib3 and requests are powerful HTTP client libraries for Python, but they have different strengths and weaknesses. Here are some benefits of using urllib3 over requests:

1. **Connection pooling**: As mentioned earlier, urllib3 automatically reuses existing connections to improve performance. While requests also supports connection pooling, urllib3's implementation is more flexible and customizable.
    
2. **Lower memory footprint**: In some scenarios, urllib3 may have a lower memory footprint than requests due to its more lightweight implementation.
    
3. **More fine-grained control**: Urllib3 provides more fine-grained control over low-level HTTP features such as retries, timeout handling, and SSL verification. This level of control can be helpful for developers who need to tailor their HTTP requests to their specific use case.
    
4. **Extensibility**: Urllib3 is designed to be extensible and supports third-party libraries for additional features, such as OAuth authentication.
    
5. **Compatibility**: Urllib3 is compatible with a wider range of Python versions, including Python 2.7 and 3.3+. This can be helpful for developers who need to support legacy Python code.
    

### Why choose Requests over Urllib3?

There are several reasons why one might choose to use requests over urllib3:

1. **Ease of use:** Requests is often considered to be more user-friendly and easier to use than urllib3. It has a simpler API and requires fewer lines of code to perform common tasks.
    
2. **Wide adoption**: Requests is one of the most widely used Python libraries for making HTTP requests, and as such, it has a large and active community of contributors and users. This can be beneficial for finding help, support, and third-party integrations.
    
3. **Higher-level feature**s: While urllib3 provides more fine-grained control over low-level HTTP features, requests offers higher-level features such as automatic decompression of compressed responses and support for streaming responses.
    
4. **Time-saving features:** Requests includes time-saving features such as automatic content decoding, which can be particularly useful when dealing with compressed response data.
    

### Conclusion

Overall, the choice between urllib3 and requests depends on the specific requirements of your project. **If you require no additional dependencies and more fine-grained control over low-level HTTP features, then urllib3 may be a better choice**. However, **if you prioritize simplicity and ease of use, requests may be a better fit.**

### Source code

%[https://github.com/nikhilakki/nikhilakki.in-blog-code-examples/tree/main/urllib3-example]