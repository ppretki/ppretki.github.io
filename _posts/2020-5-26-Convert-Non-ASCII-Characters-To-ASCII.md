---
layout: post
title: Convert Non ASCII Characters To ASCII 
---

In our work, every now and then we come across terms like [UTF-16](https://en.wikipedia.org/wiki/UTF-16) and 
[ASCII](https://en.wikipedia.org/wiki/ASCII). Both are characters encoding standards. 
*ASCII* comprises 128 code points in the range 0x0 to 0x7F while *UTF-16* on the other hand, forms the space with 1114112 code 
points in the range 0x0 to 0x10FFFF. Normally we don't spend that much time wondering about it. 
But sometimes we are forced to make such mapping: UTF-16 -> ASCII. Most, if not all, programming languages support both sorts of codding thus making our live easier if we 
have to do something around this area. 


## UTF-16 TO ASCII in Java

In Java, we have library like `org.apache.lucene` at our disposal and we won't hesitate to use it. 

First, we need to add the library to our project
~~~xml
<dependencies>
    <dependency>
      <groupId>org.apache.lucene</groupId>
      <artifactId>lucene-analyzers-common</artifactId>
      <version>8.5.1</version>
    </dependency>
  </dependencies>
~~~

then, write simple `toASCII` methods:

<script src="https://gist.github.com/ppretki/ef62c453ffb8a2e5fe783dfa9b5697b8.js?file=Main.java"></script>

and bob's your uncle, here is the expected result 

<script src="https://gist.github.com/ppretki/ef62c453ffb8a2e5fe783dfa9b5697b8.js?file=results.out"></script>

# Source
1. [lucene-analyzers-common](https://mvnrepository.com/artifact/org.apache.lucene/lucene-analyzers-common)
