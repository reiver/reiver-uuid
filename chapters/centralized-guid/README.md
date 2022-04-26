# Centralized GUID ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

There are two main strategies for creating a **globally unique identifier** (**GUID**):

* distributed, and
* centralized.

(There are also some strategies that are some form of hybrid between the two.)

Some examples of **GUID**s created using a **centralized** registry are:

* IETF RFC numbers,
* URL shortener **ID**s (under a specific Internet domain name),
* the Internet domain name system (if you include time),
* phone numbers (if you include time).

They can work.

It is possible for them to be more space-efficient.

But they also have major problems if you are not in total control over the registry.
For example — your **GUID** can be taken from you, or censored.

## UUID

**UUID**s, in general, are _NOT_ centralized.

**UUID**s, in general, are either _distributed_, or a _hybrid_.

One of the design goals of **UUID** was for them to be able to be created in a _distributed_ manner.

And with **UUID**s of type **version**=`4` and **variant**=`100` it is possible to create **UUID**s in a completely **distributed** manner.
