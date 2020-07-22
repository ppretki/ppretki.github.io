---
layout: post
title: Tests in SpringBoot 2.x 
---


# Maven

## Surefire plugin 

Executes test classes whose names ends with *Test*.

Related default lifecycle phases:
- test 

Command to execute:
```shell script
mvn test
```

## Failsafe plugin 

Executes test classes whose names ends with *IT*. Related default lifecycle phases:

- pre-integration-test	
- integration-test	
- post-integration-test

Command to execute:
```shell script
mvn test
```

>
Second, the failsafe plugin runs and verifies tests using different goals. A test failure in the integration-test phase doesn't fail the build straight away, allowing the phase post-integration-test to execute, where clean-up operations are performed.

Failed tests, if any, are only reported during the verify phase, after the integration test environment has been torn down properly.
>
--[The Maven Failsafe Plugin, Nguyen Nam Thai](https://www.baeldung.com/maven-failsafe-plugin)


## Context Caching

# References
1. [Spring Framework docs](https://docs.spring.io/spring-framework/docs/current/spring-framework-reference/testing.html#testcontext-ctx-management-caching)
2. [MergedContextConfiguration](https://github.com/spring-projects/spring-framework/blob/3a0f309e2c9fdbbf7fb2d348be861528177f8555/spring-test/src/main/java/org/springframework/test/context/MergedContextConfiguration.java#L415)

