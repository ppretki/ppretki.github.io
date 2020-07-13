---
layout: post
title: Hibernate  
---



# Hibernate Proxies


```java
@Entity
public class Customer {
    private Long id;
    private String firstName;
    private String lastName;
    @OneToOne(fetch = LAZY, cascade = ALL)
    private Address address;
}
```

![Customer Entity Structure](/images/HibernateCustomerEntityStructure.png)

## LazyInitializationException

```java
Address address = null;
try (val session = sessionFactory.openSession()) {
    val customer = session.get(Customer.class, customerId);
    address = customer.getAddress();
}
address.getStreet(); // <- session is closed
```



## Dirty Check

{% plantuml %}
@startuml
Transaction -> TransactionImpl: commit
TransactionImpl -> DefaultFlushEventListener: onFlush
DefaultFlushEventListener -> AbstractEntityPersister: findDirty(Object[] currentState, Object[] previousState)
@enduml
{% endplantuml %}
