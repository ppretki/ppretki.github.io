---
layout: post
title: Python Generators
tags: python, generators
---

# Definitions

- Iterator and Iterator Protocol
- StopIteration Exception
- Iterable
- Iterable containers
- yield Statement, Generator Function, Generator

## [Iterator and Iterator Protocol](https://docs.python.org/3/glossary.html#term-iterator)

An object representing a stream of data. An iterator implements two the methods that forms `iterator protocol`:
- `__iter__()` - returns the iterator object itself, 
- `__next__()` - returns the next item from the container.

Python has two build-in functions which allow to work with iterators:
- `iter(object)` - it calls `__iter__()` for the given object and returns an iterator, 
- `next(iterator)` - retrieves the next item from the iterator by calling its `__next__()` method

Example:
```python
class EvenNumbers:

    def __init__(self, upper_limit):
        self.upper_limit = upper_limit

    def __iter__(self):
        self.state = 0
        return self

    def __next__(self):
        self.state += 2
        if self.state > self.upper_limit:
            raise StopIteration
        return self.state
```
[StopIteration](https://docs.python.org/3/library/exceptions.html#StopIteration) exception is used to signal that no more elements exist in the stream e.g:
```python
iterator = iter(EvenNumbers(upper_limit=8))
print(next(iterator)) # = 2
print(next(iterator)) # = 4
print(next(iterator)) # = 6
print(next(iterator)) # = 8
print(next(iterator)) # StopIteration exeception is thrown here
``` 
The exception is handled by python while the iterator is used in `for` loop:
```python
for number in EvenNumbers(upper_limit=8):
    print(number) # 2, 4, 6, 8, no StopIteration exception is thrown
``` 

2. Iterable
An iterable is any object that can return an iterator.

3. Iterable containers

Containers are data structures that hold other objects. Containers allow to iterate over 
objects they contain. Lists, tuples, dictionaries, and sets are all iterable objects. 
They are iterable containers which you can get an iterator from. In order to get an 
iterator from the containers we use function `iter()`, e.g.:

```python
tuple = ("A", "B", "C")
it = iter(tuple)
print(next(it)) # = A
print(next(it)) # = B
print(next(it)) # = C
``` 

4. *yield* Statement

Can only be used in the body of a function definition. It changes function into `generator function`.
Generator function when called returns `generator`.   

```python
def even_numbers(upper_limit):
    state = 0
    while state < upper_limit:
        state += 2
        value = yield state

generator = even_numbers(8) 

next(generator) # executes all code inside generator 
                # function up to the first yield 
                # statement and freezes the state 
                # of the generator, 
generator.send("string") # passes the value back to 
                # the generator and resumes its code 
                # execution up to the next 'yield' 
                # statement occurrence  
```