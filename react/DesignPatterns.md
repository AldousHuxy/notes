# React Design Patterns

## Creational Patterns
### How objects are created
 - Singleton
   - [Singleton](https://refactoring.guru/design-patterns/singleton) is a creational design pattern that lets you ensure that a class has only one instance, while providing a global access point to this instance.
 - Prototype
 - Builder
 - Factory
## Structural Patterns
### How objects relate to each other
 - Facade
 - Proxy
## Behavioural Patterns
### How objects communicate with each other
 - Iterator
 - Observer
 - Mediator
 - State

## SOLID Patterns
 - Single-Responsibility
   - This principle states that a class should only have one responsibility. Furthermore, it should only have one reason to change.
 - Open-Closed
   - Classes should be open for extension but closed for modification. In doing so, we stop ourselves from modifying existing code and causing potential new bugs
 - Liskov Substitution
   - If class A is a subtype of class B, we should be able to replace B with A without disrupting the behavior of our program.
 - Interface Segregation
   - Larger interfaces should be split into smaller ones. By doing so, we can ensure that implementing classes only need to be concerned about the methods that are of interest to them.
 - Dependency Inversion
   - The principle of dependency inversion refers to the decoupling of software modules. This way, instead of high-level modules depending on low-level modules, both will depend on abstractions.