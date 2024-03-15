## JSON Path

- JSONPath is a query language for JSON, similar to XPath for XML.
- It allows us to extract data from JSON documents. And we can get our Expected output Easily from Large or Small JSON Documents.

### JSONPath Syntax

- Consider the below sample JSON document.

```json
{
  "store": {
    "book": [
      {
        "category": "reference",
        "author": "Nigel Rees",
        "title": "Sayings of the Century",
        "price": 8.95
      },
      {
        "category": "fiction",
        "author": "Evelyn Waugh",
        "title": "Sword of Honour",
        "price": 12.99
      },
      {
        "category": "fiction",
        "author": "Herman Melville",
        "title": "Deep River",
        "price": 8.99
      }
    ]
  }

}
```

- To extract the author of the first book, we can use the JSONPath expression `$.store.book[0].author`.
- The `$.` symbolizes the root of the JSON document.
- To get the author of all books, we can use the JSONPath expression `$.store.book[*].author`.
- The `*` symbolizes all elements in the array.
- Use [index] to access the elements of an list.
- Use .property to access the properties of an object.

### Advanced JSONPath Syntax in Kubernetes

- In Kubernetes, we can use JSONPath to extract data from the output of `kubectl get` commands.
- For example, to get the names of all pods in the default namespace, we can use the JSONPath expression `kubectl get pods -o jsonpath='{.items[*].metadata.name}'`.
- The `kubectl get` command returns a JSON document with a list of pods. The JSONPath expression `{.items[*].metadata.name}` extracts the names of all pods from the JSON document.
- Use `--custom-columns` to specify the columns to display in the output of `kubectl get` commands. For example, `kubectl get pods --no-headers --custom-columns=NAME:.metadata.name,STATUS:.status.phase` displays the names and statuses of all pods in the default namespace.
- Use `--sort-by` to sort the output of `kubectl get` commands. For example, `kubectl get pods --sort-by=.metadata.creationTimestamp` sorts the pods by creation timestamp.


Date of Commit: 15/03/2024