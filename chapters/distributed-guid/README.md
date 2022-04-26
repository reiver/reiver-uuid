# Distributed GUID ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

There are two main strategies for creating a **globally unique identifier** (**GUID**):

* distributed, and
* centralized.

(There are also some strategies that are some form of hybrid between the two.)

Some examples of **GUID**s created using a **distributed** strategy are:

* random-numbers chosen from a large-enough bit-space,
* chrono-random numbers,
* XIM,
* UUID of type **version**=`4` and **variant**=`100`.
