---
layout: post
title: Spring Security - SpringSecurityFilterChain
---

## How SpringSecurityFilterChain is integrated with Embedded Tomcat ?

![SpringSecurityFilterChain](/images/SpringSecurity_IntregrationWithEmbeddedTomcat.png)
![SpringSecurityFilterChain](/images/SpringSecurity-SpringSecurityFilterChainStackTrace.png)

## How SpringSecurityFilterChain is introduced to WebApplicationContext ?
![SpringSecurityFilterChain](/images/SpringSecurity_CreateSpringSecurityFilterChain.png)


# How SpringSecurityFilterChain is configured ?

![SpringSecurityFilterChain](/images/SpringSecurity_SpringSecurityFilterChain_Configuration.png)

# How SpringSecurityFilterChain processes Http Request ?

![SpringSecurityFilterChain](/images/SpringSecurityFilterChainSelection.png)


# HttpSecurity in examples

## Ant Matcher

```java
httpSecurity.antMatcher("/a/**");
httpSecurity.addFilterBefore(new PrintFilter("Filter A"), ChannelProcessingFilter.class);
httpSecurity.addFilterBefore(new PrintFilter("Filter B"), ChannelProcessingFilter.class);
httpSecurity.addFilterBefore(new PrintFilter("Filter C"), ChannelProcessingFilter.class);
```
GET "http://localhost:8080/a/1"

```text
AntPathRequestMatcher  : Checking match of request : '/a/1'; against '/a/**'
FirstWebSecurityConfigurerAdapter : Filter A
FirstWebSecurityConfigurerAdapter : Filter B
FirstWebSecurityConfigurerAdapter : Filter C
```



