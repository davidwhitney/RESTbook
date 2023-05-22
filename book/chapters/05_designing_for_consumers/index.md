# Designing for consumers

Consumers of APIs crave consistency. They want to be able to predict what they're going to get back from an API, and they want to be able to predict how to use it.
It's the most important thing. It's doubly important when you're growing APIs over time, and adding new resources and endpoints. If you're not consistent, you'll end up with a mess of different formats and styles, and your consumers will hate you.

Designing with consistency in mind means getting all the small details right, and then never drifting from them endpoint by endpoint.

- Cross-resource searching
- Designing for Deserialization
- Cross resource conventions
- Using media type headers to explain resource types




## Resource Microformats

### Ids and References to other resources

Systems should present and reference Ids of resources in a consistent way.

```json
{
    "id": "1234",
    "name": "John Smith"
}
```

This is the *exact same data* that should appear in your response headers.
For symmetry, the same data should also appear when objects reference this entity.

```json
{
    "personId": {
        "value": "1234",
        "type": "person",
        "href": "http://example.com/person/1234"
    },
}
```


### Summary Objects

Summary objects are the *opposite* of Microformats - they're a way of embedding a summary of a resource in another resource.

A summary object should always contain an Id, and should always contain a link to the full resource.

The rest of the summary object? That's up to you!

Summary objects are expected to contain different additional fields from resource to resource, and that's fine - they're not a standard, they're a pattern.

```json
// Order Object
{
    "id": "1234",
    "name": "John Smith",
    "personSummary": {
        "id": {
            "value": "1234",
            "type": "person",
            "href": "http://example.com/person/1234"
        },
        "someValue": "goes here",
        "someOtherValue": "goes here also"
    }
}
```


## Using Headers and Media Types to explain resources

Http is a very simple protocol, and it's not very good at explaining the structure of resources. It's very good at transferring data, but it's not very good at explaining what that data is.
We can use custom headers and custom media types to explain the structure of our resources.

You don't want to stray too far from the path here - you don't want to create a whole new protocol, or a whole new way of doing things. You just want to help provide some context to your consumers.
Headers are important because consuming clients have access to them before they even start to deserialize the response body. They can use them to make decisions about how to deserialize the response body.

They're also useful because they're easy to add to existing APIs - you can add them without breaking existing clients.

### HTTP Headers are metadata

HTTP headers are metadata about the response. They're not part of the response body, and they're not part of the protocol. They're just metadata.

The cool thing about using headers for metadata is that they're available to the client before they even start to deserialize the response body.

- They can use them to make decisions about how to deserialize the response body.
- They can use them to make decisions about how to handle the response body.
- You can use them to track usage of your API, especially if you're managing multiple versions of your API.

### What makes a good custom header?


### Using custom media types to explain resources

Options:

1. Use a custom media type for each resource
2. Use a custom header elaborating on a standard media-type

Each come with pro's and cons.

#### Use a custom media type for each resource

- Pro: You can use the media type to explain the structure of the resource
- Con: You have to create a new media type for each resource
- Con: Most applications will be expecting application/json, so you'll have to teach them to expect (and sometimes configure their infrastrucutre to not reject) your custom media type

#### Use a custom header elaborating on a standard media-type

- Pro: You can use the media type to explain the structure of the resource
- Pro: You can use the same media type for all resources, matching the expectations of the average API consumer
- Con: Custom header providing "subtype" information is non-standard
- Con: You have to teach your consumers to look for the header if they need it for deserialization

