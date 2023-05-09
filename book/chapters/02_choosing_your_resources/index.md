# Choosing your resources

Working out how you're going to represent your business or domain as a series of resources is perhaps the single most important thing you'll do when you start designing an API.

It doesn't matter if you're building an API to *represent an existing system*, or you're building a brand new system where the API itself *is the system*, the way that you both organise and design your resources and representations makes the difference between a system that can be consumed by other developers, and a system that feels absolutely incomprehensible to the outside world.

---
What makes a good resource?

A good resource tends to represent top-level entities or business processes within your system. If you're following Domain Driven Design, you'll probably be familiar with the term "aggregate root" - and generally top-level resources work best when they are representations of one of the high level concepts within your system.

- data logically owned by that aggregate root controlled by sub-resources
- operations nested below root level entities

---
Naming Resources

- Naming in urls?
- Singular or Pluralisation?


