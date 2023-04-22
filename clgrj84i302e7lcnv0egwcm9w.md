---
title: "What is JSON Schema?"
datePublished: Sat Apr 22 2023 05:20:41 GMT+0000 (Coordinated Universal Time)
cuid: clgrj84i302e7lcnv0egwcm9w
slug: what-is-json-schema
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1681564199523/cb19277f-ce98-4f62-b041-159617414f68.avif
tags: json, api-gateway, json-schema, restful-api-validation, restapi

---

I recently used JSON Schema in one of my projects for [API request validation on AWS API gateway.](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-create-model.html) I found it overwhelming at first, but quite powerful as it fit our use case quite well. Validating request before it hits your back-end system can filter out quite a lot of bad/invalid requests.

### What is JSON Schema?

JSON Schema is a way to describe the structure and validation rules for JSON data. It's a JSON document that defines the expected format, data types, constraints, and rules for the JSON data. JSON Schema can be used to ensure that the JSON data produced by an application or API conforms to a specified format, and to validate the data provided by a client.

### How to write one?

To write a JSON Schema, you need to define the properties of the JSON object you want to validate, and the rules for those properties. Here is an example of a simple JSON Schema that defines a person object with two properties, "name" and "age":

```json
{
    "$schema": "http://json-schema.org/draft-07/schema#",
    "type": "object",
    "properties": {
        "name": {
            "type": "string"
        },
        "age": {
            "type": "integer",
            "minimum": 18
        }
    },
    "required": ["name", "age"]
}
```

In this example, the `type` property is used to specify the data type of each property. The `minimum` property is used to specify a minimum value for the "age" property. The `required` property is used to specify which properties are required.

The `"$schema"` property at the top of the document specifies the version of the JSON Schema specification being used.

We can validate the schema online at [https://www.jsonschemavalidator.net/](https://www.jsonschemavalidator.net/)

![json schema validation failure](https://cdn.hashnode.com/res/hashnode/image/upload/v1681562969076/3a87b1ed-09dd-41db-b58f-7f5ff7b8178a.png align="center")

![json schema validation success](https://cdn.hashnode.com/res/hashnode/image/upload/v1681562944587/52bfab37-d004-4aa3-868c-ed56e244e12e.png align="center")

### Pros & Cons

**Pros:**

1. **Improved Data Quality:** JSON Schema provides a way to validate JSON data against a set of rules, ensuring that it conforms to the expected structure and data types. This can help to improve the overall quality of the data.
    
2. **Increased Consistency:** By enforcing a standardized structure and format for JSON data, JSON Schema can help ensure that data is consistent across different applications and systems.
    
3. **Better Documentation:** JSON Schema provides a clear and concise way to document the structure and constraints of JSON data, making it easier for developers to understand and work with the data.
    
4. **Widely Supported:** JSON Schema is a widely adopted standard, supported by many programming languages and tools, making it easy to use and integrate into existing systems.
    

**Cons:**

1. **Complexity:** JSON Schema can be complex and difficult to learn, particularly for developers who are new to the concept of data validation.
    
2. **Performance Overhead:** Validating JSON data against a JSON Schema can add additional overhead and processing time, particularly for large datasets.
    
3. **Limited Expressiveness:** While JSON Schema provides a wide range of validation rules and keywords, there are some constraints and data structures that cannot be fully expressed using JSON Schema.
    
4. **Learning Curve:** Learning how to write JSON Schema can be time-consuming, particularly for developers who are not familiar with the JSON Schema syntax and validation rules.
    

### Takeaway

JSON Schema supports a wide range of validation rules and keywords to describe complex data structures and constraints. You can find more information and examples in the JSON Schema documentation: [https://json-schema.org/learn/](https://json-schema.org/learn/)