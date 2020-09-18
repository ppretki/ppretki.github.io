---
layout: post
title: Code Testing
---


# Code Duplication in Tests

>
Readability matters. Don't try to be overly DRY . Duplication is okay, if it improves readability. Try to find a balance between DRY and DAMP code
>
-- [Ham Vocke, The Practical Test Pyramid](https://martinfowler.com/articles/practical-test-pyramid.html#WritingCleanTestCode)


>
As a principle, favor DRY in production code, favor DAMP in test code. While both are equally important, with a little wisdom you can tip the balance in your favor.
>
-- [Chris Edwards, What does “DAMP not DRY” mean when talking about unit tests?](https://stackoverflow.com/a/11837973)


>
In tests we can use the DAMP principle (“Descriptive and Meaningful Phrases”), which emphasizes readability over uniqueness. Applying this principle can introduce code redundancy (e.g., by repeating similar code), but it makes tests more obviously correct.
>
--[Derek Snyder and Erik Kuefler, Testing on the Toilet: Tests Too DRY? Make Them DAMP!](https://testing.googleblog.com/2019/12/testing-on-toilet-tests-too-dry-make.html)


# Techniques

# Time in Unit Tests
[Kafka, Time](https://github.com/apache/kafka/blob/fc5f6b0e46ff81302b3e445fed0cdf454c942792/clients/src/main/java/org/apache/kafka/common/utils/Time.java#L23)



1. [ddd-by-examples/library](https://github.com/ddd-by-examples/library/blob/master/src/integration-test/groovy/io/pillopl/library/lending/patronprofile/web/PatronProfileControllerIT.java)
2. [When Code Duplication Is Acceptable](https://hackernoon.com/when-code-duplication-is-acceptable-51ce33ecd0f5)
3. [Rule of three](https://en.wikipedia.org/wiki/Rule_of_three_(computer_programming))
4. [Wildfly Integration Test](https://github.com/wildfly/wildfly/blob/master/testsuite/integration/web/src/test/java/org/jboss/as/test/integration/web/sharedsession/SharedSessionTestCase.java)
5. [Unclebob, fitnesse](https://github.com/unclebob/fitnesse/blob/master/test/fitnesse/http/RequestTest.java)