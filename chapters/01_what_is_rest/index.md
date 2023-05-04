# What is REST (the simple version)?

REST is a style of building Web APIs.

**REST APIs all share specific characteristics** that make programming against them easy, along with a series of constraints that are designed to **guide the design** of the APIs that we build.

REST describes a style of APIs where you interact with **representations** (usually JSON or XML documents) and associated metadata of **resources** (some entity that lives in your system) using **resource identifiers** (URLs).

For example, if you were to design an API that could be requested like this:

```bash
GET https://tempuri.org/v1/weather
HOST: tempuri.org
Accept: application/json
```

That returned a response that looked like this:

```bash
HTTP/1.1 200 OK
Content-Type: application/json

{
    "temp": 70,
    "humidity": 50,
    "pressure": 30
}
```

You would be fetching the **JSON representation** of the current weather **resource** using the **resource identifier** `https://tempuri.org/v1/weather`. 

If you’ve built software on the web, you’ve **used RESTful APIs before** - but more importantly, if you’ve **ever browsed the web** you’ve used REST, because as an architectural style, it **describes how regular webservers work.**

There’s often confusion regarding “what makes an API RESTful” because **while “the web” is RESTful by default, not everything that talks HTTP is RESTful**. Because of this, the definition of REST outlines some **constraints** - these constraints describe how your APIs should behave, and what properties they must exhibit (e.g., “REST APIs are stateless, so don’t rely on session state”) which differentiates them from “other styles of APIs that can be invoked over HTTP”. By building APIs which exhibit RESTful properties, we **work with the programming style of HTTP**, rather than build APIs that are coincidentally invoked over it.

We build APIs in a RESTful style, because when we do, the APIs are generally explicable, unsurprising, scalable and most importantly easy to program against.

**REST APIs are the lingua franca of the web** and help people building on top of them fall into the pit of success.

---
# What is REST (the complicated version)?

REST (Representational State Transfer) is an **architectural style for designing networked applications**. It was introduced by Roy Fielding in his 2000 doctoral dissertation as a way to promote scalable, maintainable, and flexible applications using the web's infrastructure.

While it was **presented in 2000**, the definitions presented in the dissertation **described the state of the developing web at the time** during the standardisation of HTTP by the IETF (Internet Engineering Task Force) of the W3C - in a sense, REST was as much a description of how the web **actually worked** than just a promoted architectural style.

Fielding's dissertation on architectural styles describes many other ways for building software, and the [section on REST](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm) is only about ~7k words / 20 pages long - providing a good starting point for anyone designing software for the web.

## REST is an exercise in constraints.

The REST architectural style is described as a **series of constraints** - where any system that complies to some or all of them can be described as RESTful.

These constraints are:

- RESTful applications are **Client-Server** in design, separating the UI from data storage and processing logic.
- RESTful applications are **Stateless** in nature - with each request containing all the information necessary, with any required session state stored on the client. Stateless design here is designed to increase reliability and scalability.
- Consumers of RESTful applications are expected to **Cache** data and responses, following guidance and hints provided by the application. This caching constraint **counteracts the network performance penalties** that inherently come with stateless application designs which require additional data per-request.
- RESTful applications **adhere to a Uniform Interface** - meaning that all REST applications can be interacted with in a similar way.
- RESTful systems support **Layering** of system capabilities - where components can be layered together to produce more complex abstractions (e.g., a load-balancer fronting a HTTP API) without each layer being exposed to each others implementation.
- RESTful systems support **Code on Demand** - where the application can extend the functionality of a client by transferring executable code (e.g., JavaScript) to the client to be executed.

While all of those constraints are important, the most important constraint is the **Uniform Interface** constraint - which is the one that most people think of when they think of REST as it describes the **interface** of the API.

## The “Uniform Interface” of REST

REST is defined by four interface constraints:

- Identification of resources
- Manipulation of resources through representations
- Self-descriptive messages
- Hypermedia as the engine of application state.

and all of them are concerned with how you identify, interact with, and describe **resources**.

# Resources and Representations

Resources in REST are the **core abstraction** - with anything that you can name and identify being a resource. Documents are resources, images, concepts, outputs of services, even empty collections are resources. Importantly resources can be mapped to one or more URLs - with one of those URLs being the **primary identifier** of a resource.

This may appear vague at first, but this generality allows REST to be applied to a diverse set of systems and interactions - it's generality is one of the reasons why REST is so popular.

Fielding's dissertation describes the data elements in REST as:

| Data Element	            | Modern Web Examples 
----------------------------|----------------------
| resource                  | the intended conceptual target of a hypertext reference
| resource identifier       | URL, URN
| representation            | HTML document, JPEG image
| representation metadata   | media type, last-modified time
| resource metadata         | source link, alternates, vary
| control data              | if-modified-since, cache-control

In practice, in most RESTful HTTP APIs these data elements are satisified in the following way:

| Data Element	            | Modern Web Examples 
----------------------------|----------------------
| resource                  | A Domain entity in a system (e.g., a User, a Product, a Purchase) and operations it can perform (e.g., a Purchase can be cancelled)
| resource identifier       | Almost always URL
| representation            | Usually a JSON response document representing the resource data
| representation metadata   | Content-Type HTTP headers along with last-modified times or ETags
| resource metadata         | Frequently omitted in most HTTP APIs
| control data              | if-modified-since and cache-control HTTP headers where Caching is well supported

Because REST is a style, not a standard, there's no strict rules on how you should design your resources, and what they should look like - for the rest of this book we're going to dive into the low level detail and trade-offs of designing resources, 
