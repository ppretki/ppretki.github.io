---
layout: post
title: Abstractions in Java
---

# Interfaces are not abstractions
>
Interfaces are not abstractions
An interface is just a language construct. In essence, it's just a shape.
Having only one implementation of a given interface is a code smell.
>
-- [Mark Seemann](https://blog.ploeh.dk/2010/12/02/Interfacesarenotabstractions/#:~:text=Having%20only%20one%20implementation%20of,Interfaces%20are%20not%20abstractions.&text=An%20interface%20is%20just%20a%20language%20construct.)

# Reused Abstractions Principle
>
Abstractions are found during refactoring.
Discovery of abstractions implies that abstractions are used more than once. Super classes have more than one subclass. Interfaces are implemented more than once. Abstract methods are overridden multiple times. And so on.
>
-- [Jason Gorman](http://www.codemanship.co.uk/parlezuml/blog/?postid=934)


## Header Interfaces
>
A header interface is an explicit interface that mimics the implicit public interface of a class. Essentially you take all the public methods of a class and declare them in an interface.
>
-- [Martin Folwer](https://martinfowler.com/bliki/HeaderInterface.html)

## Role Interface
>
A role interface is defined by looking at a specific interaction between suppliers and consumers. A supplier component will usually implement several role interfaces, one for each of these patterns of interaction. This contrasts to a HeaderInterface, where the supplier will only have a single interface.
>
-- [Martin Folwer](https://martinfowler.com/bliki/RoleInterface.html)

>
Role interfaces follow Interface Segregation Principle but header interfaces do not.
>
-- [Martin Folwer](https://martinfowler.com/bliki/RoleInterface.html)

