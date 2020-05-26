---
layout: post
title: Convert Non ASCII Characters To ASCII 
---

In Java programming language characters are encoded using UTF-16 standard. Sometimes we need to 
convert `String` to ASCII standard. What this basically means is that we need to define mapping 
between one set containing large number of elements (UTF-16) to much smaller set containing only 
(ASCII). From mathematical point of view this is not a trivial problem since there exists an infinite 
number of such potential mappings. Fortunately we are not mathematician but software developers.
We have library like `org.apache.lucene` at our disposal and we won't hesitate to use it. 


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

<script src="https://gist.github.com/ppretki/ef62c453ffb8a2e5fe783dfa9b5697b8?file=Main.java"></script>

and bob's your uncle, here is the expected result 

<script src="https://gist.github.com/ppretki/ef62c453ffb8a2e5fe783dfa9b5697b8?file=results.out"></script>

# Source
1. [lucene-analyzers-common](https://mvnrepository.com/artifact/org.apache.lucene/lucene-analyzers-common)
