# Chrono Random ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

One strategy for creating a **globally unique identifier** (**GUID**) is by using **random numbers** chosen from a space that is large-enough.

You just implemented this strategy for **UUID**s with your `uuid.Random()` function.

Although this strategy is _good_, some people don't feel this strategy is _good enough_.

They worry that with enough people creating **GUID**s in the future, someone could re-create an already create (randomly create) **GUID**.

These chances of that happening is very very very small, but it isn't zero.

## Time ++ Randomness

A way you can deal with this concern is incorporate both **time** and **random numbers** into your **GUID**.

**Infact, this is the method I used to create GUIDs back in the 1990s, before I ever heard of UUIDs.**

Let's first look at this in general, and then look at how we can implement this for **UUID**s.

## String Example

We need 2 things to construct this type of **GUID**:

* the **current time**, and
* a **random number**.

From an implementation point-of-view, you will also care about **what format the time is in**, and **the bit size of the random number**.
But can worry about those 2 details later.

Let's say the **current time** is:
```golang
"2022-03-30T02:35:46Z"
```

(I used **UTC** format for the time here, as lexical (string) ordering of UTC time is also chronological ordering. Which is a very nice property.)

And let's say that the **random number** we draw is:
```golang
"e5UTcWYaZeVN-C-SpQTJG6RWwzfZCJqbC7ZbC7bAutxK6j7ZRtTTJP9nOTFBOdl5WzssKxI99uc2l9aS9srRDw"
```
(I used **base64url** binary-to-text encoding for the random number here.)

We could then combine these 2 strings to create our _chromo random_ **GUID**.

There are a lot of different ways we could combine them.
Here is one of them:
```
<current time> ++ "_" ++ <randomness>
```

So, using our previous example, we could get:
```golang
"2022-03-30T02:35:46Z_e5UTcWYaZeVN-C-SpQTJG6RWwzfZCJqbC7ZbC7bAutxK6j7ZRtTTJP9nOTFBOdl5WzssKxI99uc2l9aS9srRDw"
```

This _could_ work as a _chrono random_ **GUID**, but it is space inefficient.

We be more space efficient if we combine the _current time_ and the _randomness_ together as binary.

## Binary Time

There are different ways of story **time** as binary.

How many **bits** do we use to story time?

What is the smallest **resolution** that can be represented?
A second?
A nanosecond?
A picosecond?
Etc?

What time does **zero** represent?

These are just decisions that one needs to make. 
(Likely influenced by what the computers you have to deal with are capable of now, and whatever future you are trying to future-proof for.)
