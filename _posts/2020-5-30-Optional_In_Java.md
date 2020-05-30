---
layout: post
title: Optional In Java 
---


>
An optional is essentially an immutable collection that can hold at most one element. Optional<T> does not implement Collection<T> , but it could in principle.

You should declare a method to return Optional<T> if it might not be able to return a result and clients will have to perform special processing if no result is returned

You should never use optionals as map values. If you do, you have two ways of expressing a key’s logical absence from the map: either the key can be absent from the map, or it can be present and map to an empty optional. This represents needless complexity with great potential for confusion and errors. More generally, it is almost never appropriate to use an optional as a key, value, or element in a collection or array.
>
-- [Joshua Bloch](https://www.amazon.com/Effective-Java-Joshua-Bloch/dp/0134685997)

>
It is important to note that the intention of the Optional class is not to replace every single null reference. Instead, its purpose is to help design more-comprehensible APIs so that by just reading the signature of a method, you can tell whether you can expect an optional value. This forces you to actively unwrap an Optional to deal with the absence of a value.
>

-- [Oracle Technical Resources](https://www.oracle.com/technical-resources/articles/java/java8-optional.html).

> 
Our intention was to provide a limited mechanism for library method return types where there needed to be a clear way to represent "no result", and using null for such was overwhelmingly likely to cause errors.

For example, you probably should never use it for something that returns an array of results, or a list of results; instead return an empty array or list. You should almost never use it as a field of something or a method parameter. 

I think routinely using it as a return value for getters would definitely be over-use.
>

-- [Brian Goetz](https://stackoverflow.com/a/26328555)

# Source
1. [Joshua Bloch, Effective Java 3rd Edition](https://www.amazon.com/Effective-Java-Joshua-Bloch/dp/0134685997)
2. [Oracle Technical Resources](https://www.oracle.com/technical-resources/articles/java/java8-optional.html).
3. [Brian Goetz, Java Language Architect at Oracle.](https://stackoverflow.com/a/26328555)
