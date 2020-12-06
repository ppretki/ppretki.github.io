---
layout: post title: Software Modularization
---

# Modularization
>
The modularizations are intended to describe the design decisions which must be made before
the work on independent modules can begin.
>
-- [On the criteria to be used in decomposing systems into modules](https://prl.ccs.neu.edu/img/p-tr-1971.pdf)


# Separation of concerns

>
A concern is a set of information that affects the code of a computer program.
>
--[wikipedia](https://en.wikipedia.org/wiki/Separation_of_concerns)

# Modules

>
MODULES give people two views of the model: They can look at detail within a MODULE without being overwhelmed by the
whole, or they can look at relationships between MODULES in views that exclude interior detail
>
-- [Eric Evans](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215)

>
Modular programming is a software design technique that emphasizes separating the functionality of a program into
independent, interchangeable modules, such that each contains everything necessary to execute only one aspect of the
desired functionality
>
-- [wikipedia](https://en.wikipedia.org/wiki/Modular_programming)

>
You want your modules to work so that if I need to change part of a system, most of the time I only need to understand a
small part of that system to make the change, and I can find that small part pretty easily
>
-- [Strong Module Boundaries, Martin Fowler](https://martinfowler.com/articles/microservice-trade-offs.html)

>
There are several ways to describe coupling, but it boils down to this: If changing one module in a program requires
changing another module, then coupling exists.
>
-- [Reducing Coupling, Martin Fowler](https://www.martinfowler.com/ieeeSoftware/coupling.pdf)

>
The code that changes together, stays together. We want the functionality grouped in such a way that we can make changes
in as few places as possible. Expose as little as possible from a module. Once something becomes part of a module
interface, it’s hard to walk that back. But if you hide it now, you can always decide to share it later
>
-- [Monolith to Microservices](https://www.amazon.com/Monolith-Microservices-Evolutionary-Patterns-Transform/dp/1492047848)

# Modularity and deletion

>
To determine if a feature or aspect of a program is modular, just ask yourself this question: How many steps does it
take to delete this feature? The fewer the steps, the more modular it is. If it takes only one step to delete a
feature (usually by deleting a directory), then you can say that the design has maximum modularity.
>
-- [Modularity and deletion](http://www.javapractices.com/topic/TopicAction.do?Id=285)

# Benefits of modular programming
>
Development time should be shortened because separate groups can work on each module (microservice) with little need for
communication

Product flexibility — it is possible to make quite drastic changes or improvements in one module without changing others

Comprehensibility - system could be studied a module at a time with the result that the whole 
system could be better designed because it was better understood
>
-- [On the criteria to be used in decomposing systems into modules](https://prl.ccs.neu.edu/img/p-tr-1971.pdf)


