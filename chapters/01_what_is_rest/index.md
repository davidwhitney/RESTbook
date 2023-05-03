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


## The “Uniform Interface” of REST

REST is defined by four interface constraints:

- Identification of resources
- Manipulation of resources through representations
- Self-descriptive messages
- Hypermedia as the engine of application state.

