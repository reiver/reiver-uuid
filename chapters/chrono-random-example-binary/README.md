# Example Binary Chrono Random GUID ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

Even if our convention for chrono-random **GUID**s has a more human-readable format, it doesn't mean we have to store it in that format.

For example, even though we write the following integer as:
```
115792089237316195423570985008687907853269984665640564039457584007913129639935
```

We don't actually store it this human-readable format — (in ASCII / UTF-8) as 78 bytes:
```
31 31 35 37 39 32 30 38 39 32 33 37 33 31 36 31 39 35 34 32 33 35 37 30 39 38 35 30 30 38 36 38
37 39 30 37 38 35 33 32 36 39 39 38 34 36 36 35 36 34 30 35 36 34 30 33 39 34 35 37 35 38 34 30
30 37 39 31 33 31 32 39 36 33 39 39 33 35
```
We instead usually store it efficiently as 8 bytes in a machine-readable format:
```
ff ff ff ff ff ff ff ff
```

The same can be true for our convention for a chrono-random **GUID** —  we could be more space efficient with how we store and combine the _current time_ and the _randomness_.

## Binary Time Conventions

There are different ways of store **time** as binary.

How many **bits** do we use to store time?

What is the smallest **resolution** that can be represented?
A second?
A nanosecond?
A picosecond?
Etc?

Is there a **zero** value?
And if “yes”, what time does **zero** represent?

Does the representation have values _before_ **zero**?

Etc.

These are just decisions that one needs to make when coming up with a format and convention.
(Likely influenced by what the computers you have to deal with are capable of now, whatever future you are trying to future-proof for, plus likely what is familiar & easier for you, and some arbitrary choices, etc.)

## Unix Time

**Unix Time** is an example of a type of binary time representation that became popular with the rise of popularity of Unix & Linux.

Traditionally **unix time**:

* encoded time into **32-bits**,
* has a **resolution** of **seconds**,
* has **zero** represent **1970-01-01T00:00:00Z**,
* can represent values _before_ its **zero** value.

## Unix Time's Epochalypse

32-bit **unix time** has a **year 2038 problem** — basically, the latest time 32-bit **unix time** can represent is Tuesday January 19th, 2038 at 03:14:07 UTC (i.e., 2038-01-19T03:14:07Z ).

If we were to use **unix time** for our **binary time** for our **GUID**, to deal with its **year 2038 problem** (i.e., its **epochalypse**), we might use **64-bit** **unix time** (rather than **32-bit** **unix time**).

Many Unix & Linux systems have already switched from 32-bit **unix time** to 64-bit **unix time**, so we are using the same solution as others.

Note that 64-bit **unix time** doesn't get rid of the epochalypse! But it does push the epochalypse far far into the future. And thus would make our **GUID** format be useful longer.

So, for example, if our MSB 32-bit unix time was:
```
62 6C A0 82
```
Then our MSB 64-bit unix time would be:
```
00 00 00 00 62 6C A0 82
```

## Randomness

For the **randomness**, we just need to pick how many bytes of randomness we want.

It needs to be _large-enough_.

For the sake of our example, we will just pick 64-bits of randomness.
So, for example, here are 8 random bytes:
```
b3 d0 6b 9d 9b fe 96 6e
```

## Chrono Random

So, given that we have chosen to use **64-bit** **unix time** for our **binary time**, and use **64-bits** (i.e., 8 bytes) of **randomness**, then —

If our **current time** was **Saturday April 30th at 02:35:46 GMT**, as 64-bit **unix time** this would be (in hexadecimal):
```
00 00 00 00 62 6C A0 82
```

And if our 8 bytes of **randomness** is:
```
b3 d0 6b 9d 9b fe 96 6e
```

Then we could combine them with the **current time** first, and the **randomness** last, to get:
```
00 00 00 00 62 6C A0 82 b3 d0 6b 9d 9b fe 96 6e  
\_____________________/ \_____________________/
           |                       |
      current time              randomness
```

(Of course, we could have done this many other ways. But we just picked a way.)

## Do It Again

Let's see that again, but with a different _current-time_ and _randomness_.

Let's say our _current-time_ is:
```
2022-05-02T00:57:03Z
```
And thus our MSB 64-bit unix time is:
```
00 00 00 00 62 6F 2C 5F
```

And let's say our _randomness_ is:
```
7c bc 47 1e 95 6b b9 cc
```

Then when we combine this we get our our chrono-random **GUID**:
```
00 00 00 00 62 6F 2C 5F 7c bc 47 1e 95 6b b9 cc
\_____________________/ \_____________________/
           |                       |
      current time              randomness

```
