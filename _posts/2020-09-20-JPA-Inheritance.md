---
layout: post
title: JPA - Inheritance 
---

Class Diagram:

![PackagePolymorphism](/images/PackagePolymorphism.jpg)


# InheritanceType.SINGLE_TABLE

The strategy maps all entities of the inheritance structure to the same database table.
- Polymorphic queries very efficient
- Impossible to use not null constraints on any column that isn’t mapped to all entities
- annotations: @DiscriminatorColumn, @DiscriminatorValue

## Relational Model

![SINGLE_TABLE](/images/shoporder.jpg)

## Polymorphic query
```sql
select 
  shoporder0_.id as id2_0_, 
  shoporder0_.total as total3_0_, 
  shoporder0_.discount as discount4_0_, 
  shoporder0_.address as address5_0_, 
  shoporder0_.order_type as order_ty1_0_ 
from 
  ShopOrder shoporder0_
```

## Execution Plan

![JOINED](/images/explain_plan_1600606089660.svg)

# InheritanceType.JOINED

## Relational Model

![JOINED](/images/discountedorder-join.jpg)

## Polymorphic query
```sql
select 
  shoporder0_.id as id1_2_, 
  shoporder0_.total as total2_2_, 
  shoporder0_1_.discount as discount1_0_, 
  shoporder0_2_.address as address1_1_, 
  case when shoporder0_1_.id is not null then 1 when shoporder0_2_.id is not null then 2 when shoporder0_.id is not null then 0 end as clazz_ 
from 
  ShopOrder shoporder0_ 
  left outer join DiscountedOrder shoporder0_1_ on shoporder0_.id = shoporder0_1_.id 
  left outer join FreeDeliveryOrder shoporder0_2_ on shoporder0_.id = shoporder0_2_.id
```

## Execution Plan

![JOINED](/images/explain_plan_1600586300183.svg)


# InheritanceType.TABLE_PER_CLASS

## Relational Model

![TABLE_PER_CLASS](/images/discountedorder.jpg)

## Polymorphic query
```sql
select 
  shoporder0_.id as id1_2_, 
  shoporder0_.total as total2_2_, 
  shoporder0_.discount as discount1_0_, 
  shoporder0_.address as address1_1_, 
  shoporder0_.clazz_ as clazz_ 
from 
  (
    select 
      id, 
      total, 
      discount, 
      null :: varchar as address, 
      1 as clazz_ 
    from 
      DiscountedOrder 
    union all 
    select 
      id, 
      total, 
      null :: numeric as discount, 
      address, 
      2 as clazz_ 
    from 
      FreeDeliveryOrder
  ) shoporder0_
```

## Polymorphic query
![JOINED](/images/explain_plan_1600605925355.svg)

# References
1. [Enterprise JavaBeans 3.0 Final Release(persistence)](https://download.oracle.com/otndocs/jcp/ejb-3_0-fr-oth-JSpec/)
2. [Thorben Janssen, Inheritance Strategies with JPA and Hibernate – The Complete Guide](https://thorben-janssen.com/complete-guide-inheritance-strategies-jpa-hibernate/)
