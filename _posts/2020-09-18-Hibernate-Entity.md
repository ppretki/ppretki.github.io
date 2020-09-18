---
layout: post
title: Hibernate - Entity 
---

# Identity

## Surrogate Id
>
Surrogate keys are generated independently of the current row data, so the other column constraints may freely evolve according to the application business requirements.
>
-- [Vlad Mihalcea, A beginner’s guide to natural and surrogate database keys](https://vladmihalcea.com/database-primary-key-flavors/)

## Natural Id
>
Natural key uniqueness is enforced by external factors
>
-- [Vlad Mihalcea, A beginner’s guide to natural and surrogate database keys](https://vladmihalcea.com/database-primary-key-flavors/)


# Equals and HashCode
>
Equals and hashCode must behave consistently across all entity state transitions
>
--[Vlad Mihalcea](https://vladmihalcea.com/how-to-implement-equals-and-hashcode-using-the-jpa-entity-identifier/)

# References
1. [Vlad Mihalcea, A beginner’s guide to natural and surrogate database keys](https://vladmihalcea.com/database-primary-key-flavors/)
2. [Vlad Mihalcea, How to implement equals and hashCode using the JPA entity identifier (Primary Key)](https://vladmihalcea.com/how-to-implement-equals-and-hashcode-using-the-jpa-entity-identifier/)
