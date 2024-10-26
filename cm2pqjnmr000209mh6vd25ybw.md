---
title: "JSON manipulation in Go"
datePublished: Sat Oct 26 2024 05:43:36 GMT+0000 (Coordinated Universal Time)
cuid: cm2pqjnmr000209mh6vd25ybw
slug: json-manipulation-in-go
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1729921357207/325a7575-5afa-4b85-9d5d-6a7ceaf6ea81.png
tags: go, json, json-in-go, manipulate-json-in-go, jsongo, go-json

---

Dealing with JSON manipulation in Go can involve several approaches, depending on the complexity of your JSON data, the desired performance, and how strict you want to be with your data structures. Below are some common methods:

### 1\. **Struct-based Encoding and Decoding**

The most idiomatic way to handle JSON in Go is by mapping JSON data directly to strongly-typed Go structs. This provides compile-time safety and clear structure.

#### Example:

```go
type Person struct {
    Name  string `json:"name"`
    Age   int    `json:"age"`
    Email string `json:"email,omitempty"`
}
// Encode (marshal)
person := Person{Name: "John", Age: 30, Email: "john@example.com"}
jsonData, _ := json.Marshal(person)
// Decode (unmarshal)
var decodedPerson Person
json.Unmarshal(jsonData, &decodedPerson)
```

### Advantages:

* **Strong typing**: Fields are directly mapped to Go types.
    
* **Validation**: Go's type system ensures data is correctly structured.
    
* **Compile-time checks**: Errors in field types are caught early.
    

### 2\. `map[string]interface{}` for Dynamic or Unknown JSON

If you are dealing with dynamic or unknown JSON structures (like in APIs or flexible schemas), you can use a `map[string]interface{}` to handle arbitrary key-value pairs.

#### Example:

```go
var data map[string]interface{}
jsonStr := `{"name": "John", "age": 30, "email": "john@example.com"}`

json.Unmarshal([]byte(jsonStr), &data)
fmt.Println(data["name"], data["age"]) // Output: John 30
```

### Advantages:

* **Flexibility**: Suitable for JSON with unknown or dynamic structures.
    
* **Ad-hoc manipulation**: You can dynamically access and modify fields.
    

### Disadvantages:

* **Lack of type safety**: You need to perform type assertions manually.
    
* **Error-prone**: More runtime errors may occur, e.g., wrong type assumptions.
    

### 3\. `RawMessage` for Deferred JSON Parsing

For partial parsing or when you need to manipulate a portion of JSON without fully unmarshaling it, you can use `json.RawMessage`. This allows delaying or conditionally parsing part of the JSON data.

#### Example:

```go
type Envelope struct {
    Type string          `json:"type"`
    Data json.RawMessage `json:"data"`
}

// Partial decode
jsonStr := `{"type": "person", "data": {"name": "John", "age": 30}}`
var env Envelope
json.Unmarshal([]byte(jsonStr), &env)

if env.Type == "person" {
    var person Person
    json.Unmarshal(env.Data, &person)
    fmt.Println(person.Name, person.Age) // Output: John 30
}
```

### Advantages:

* **Lazy parsing**: You can avoid parsing unnecessary parts of the JSON.
    
* **Flexibility**: Great for handling complex APIs with different payloads.
    

### 4\. **Third-Party Libraries for More Complex Operations**

For more advanced JSON handling, such as querying or mutating JSON paths, you can use libraries like:

* [`github.com/tidwall/gjson`](http://github.com/tidwall/gjson) (for fast JSON querying)
    
* [`github.com/buger/jsonparser`](http://github.com/buger/jsonparser) (for efficient JSON parsing)
    
* [`github.com/yalp/jsonpath`](http://github.com/yalp/jsonpath) (for JSONPath expressions)
    

#### Example using `gjson`:

```go
import "github.com/tidwall/gjson"

jsonStr := `{"name": "John", "age": 30, "address": {"city": "New York"}}`
name := gjson.Get(jsonStr, "name").String()         // Get "John"
city := gjson.Get(jsonStr, "address.city").String() // Get "New York"
fmt.Println(name, city)
```

### Advantages:

* **Efficiency**: Some libraries are faster and optimized for large JSON data.
    
* **Path queries**: Libraries like `gjson` allow querying specific fields with dot notation.
    

### 5\. **Streaming JSON with** `json.Decoder`

For handling very large JSON data or when working with streams, Go’s `json.Decoder` can be used to read the JSON incrementally without loading it entirely into memory.

#### Example:

```go
file, _ := os.Open("large.json")
defer file.Close()

decoder := json.NewDecoder(file)
for decoder.More() {
    var person Person
    decoder.Decode(&person)
    fmt.Println(person.Name, person.Age)
}
```

### Advantages:

* **Memory-efficient**: Useful for large JSON data that cannot fit into memory at once.
    
* **Streaming**: Allows you to process JSON as it's being read.
    

### 6\. **Custom Marshal/Unmarshal Methods**

You can define custom JSON encoding/decoding behavior by implementing the `json.Marshaler` and `json.Unmarshaler` interfaces. This is useful when you need fine-grained control over how JSON is generated or parsed.

#### Example:

```go
type CustomPerson struct {
    Name  string
    Age   int
}
// Custom unmarshal
func (cp *CustomPerson) UnmarshalJSON(data []byte) error {
    var aux struct {
        Name string `json:"name"`
        Age  int    `json:"age"`
    }
    err := json.Unmarshal(data, &aux)
    if err != nil {
        return err
    }
    cp.Name = strings.ToUpper(aux.Name) // Custom logic: make the name uppercase
    cp.Age = aux.Age
    return nil
}
```

### Advantages:

* **Custom behavior**: Allows special formatting or validation rules during marshaling/un-marshaling.
    
* **Encapsulation**: Keeps complex logic within the struct.
    

---

### Conclusion:

* For structured JSON data: use **struct-based** encoding/decoding.
    
* For dynamic or flexible JSON: use `map[string]interface{}`.
    
* For partial or deferred parsing: use `json.RawMessage`.
    
* For very large JSON or streams: use `json.Decoder`.
    
* For advanced querying or manipulation: consider third-party libraries like `gjson`.
    
* For custom handling: implement **custom marshaling/un-marshaling**.
    

Choose the method based on your specific needs—performance, flexibility, and type safety.

**Image attribution**

[Jason Bourne image](https://www.google.com/url?sa=i&url=https%3A%2F%2Fscreenrant.com%2Fjason-bourne-movies-in-order%2F&psig=AOvVaw28eOUaBUvZ9Vg_0Hbs5oD-&ust=1730007671019000&source=images&cd=vfe&opi=89978449&ved=0CBQQjRxqFwoTCLCWsveqq4kDFQAAAAAdAAAAABAE)

[Image #2](https://www.freepik.com/free-vector/boss-manipulating-employee_902031.htm#fromView=search&page=1&position=1&uuid=fee08083-c645-47b1-9ef8-5be3d038cde4)

[Go logo](https://en.wikipedia.org/wiki/Go_%28programming_language%29#/media/File:Go_Logo_Blue.svg)