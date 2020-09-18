---
layout: post
title: Domain Driven Design - Aggregate
---

# Invariants
>
An invariant is a business rule that must always be consistent. 
>
-- [Vaughn Vernon](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)

# Aggregate
>
Aggregate is synonymous with transactional consistency (immediate and atomic) boundary. When trying to discover the Aggregates in a Bounded Context, we must understand the model’s
true invariants. Only with that knowledge can we determine which objects should be clustered into a given Aggregate. 
>
-- [Vaughn Vernon](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)

## Aggregate vs Transactions
>
Properly designed Aggregate is one that can be modified in any way required by the business with its
invariants completely consistent within a single transaction. And a properly designed Bounded Context
modifies only one Aggregate instance per transaction in all cases.
>
-- [Vaughn Vernon](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)


# References
1. [Implementing Domain-Driven Design, Vaughn Vernon](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)