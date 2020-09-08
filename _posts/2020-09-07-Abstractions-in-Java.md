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


## Header Interfaces
>
A header interface is an explicit interface that mimics the implicit public interface of a class. Essentially you take all the public methods of a class and declare them in an interface.
>
-- [Martin Folwer](https://martinfowler.com/bliki/HeaderInterface.html)


# Reused Abstractions Principle
>
Abstractions are found during refactoring.
Discovery of abstractions implies that abstractions are used more than once. Super classes have more than one subclass. Interfaces are implemented more than once. Abstract methods are overridden multiple times. And so on.
>
-- [Jason Gorman](http://www.codemanship.co.uk/parlezuml/blog/?postid=934)