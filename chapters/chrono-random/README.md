# Chrono Random ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

As I mentioned before — one **distributed** method of creating a **globally unique identifier** (**GUID**) is with **random numbers** chosen from a space that is large-enough.

For example, randomly pick a number between `0` and `115,792,089,237,316,195,423,570,985,008,687,907,853,269,984,665,640,564,039,457,584,007,913,129,639,935`. That number range is huge!!

When you created your `uuid.Random()` function you implemented this type strategy for **UUID**s.

Although this strategy is _good_, some people don't feel this strategy is _good enough_.

They worry that with enough people creating **GUID**s in the future, someone could re-create an already created (randomly created) **GUID**.

The chances of that happening is very very very small — but it isn't zero.
So, even though it is very very very unlikely to happen — it actually _could_ happen.
And some people consider this is problem enough that they choose to try to address it.

## Time & Randomness

A way you can deal with this concern is to incorporate both **time** and **randomness** into your **GUID**.

**Infact, back in the 1990s and early 2000s when I was creating GUIDs this — chrono-random method of concatenating the current-time and randomness to create a GUID — is the method I used.** (This was before I ever heard **UUID**s.)

## String Example

Let's look at example of a chrono-random **GUID** try to make all this clearer.
This first example will NOT be a **UUID**.
But I think it will help make chrono-random **GUID**s make more sense if I show you this first.

We need 2 things to construct a chrono-random **GUID**:

* the **current time**, and
* a **randomness**.

### String Example: Current Time

Let's say the **current time** is — **Saturday April 30th at 02:35:46 GMT**.

As a string, I could express this time in a number of different ways.
Here are some examples:

| Format Name | Formatted Time                   |
|-------------|----------------------------------|
| GMT         | 2022-04-30T02:35:46Z             |
| ISO 8601    | 2022-04-30T02:35:46+00:00        |
| RFC 822     | Sat, 30 Apr 2022 02:35:46 +0000  |
| RFC 2822    | Saturday, 30-Apr-22 02:35:46 UTC |
| Unix Time   | 1651286146                       |

You could even create your own time format.
I'm sure you can imagine a lot of different ways of expressing this time.

For the sake of this example, I'm just going to choose _GMT_:
```
2022-04-30T02:35:46Z
```

### String Example: Randomness

Now we need some randomness.

For the sake of this example, we will just get 32 random bytes:
```
b3 d0 6b 9d 9b fe 96 6e 02 ca 0b 83 c5 3b 52 1b 
da 59 e4 e5 f1 2c fe 32 00 35 fc 57 65 16 28 c8 
```

With this too, we can express this in different ways:

| Format Name         | Formatted Bytes                                                               |
|---------------------|-------------------------------------------------------------------------------|
| Hexadecimal         | b3d06b9d9bfe966e02ca0b83c53b521bda59e4e5f12cfe320035fc57651628c8              |
| Hexadecimal Literal | 0xb3d06b9d9bfe966e02ca0b83c53b521bda59e4e5f12cfe320035fc57651628c8            |
| Decimal             | 81332246821877457271626536020409467157667622911098444505732082021122748852424 |
| base32              | WPIGXHM372LG4AWKBOB4KO2SDPNFTZHF6EWP4MQAGX6FOZIWFDEA====                      |
| base64              | s9BrnZv+lm4CyguDxTtSG9pZ5OXxLP4yADX8V2UWKMg=                                  |
| base64url           | s9BrnZv-lm4CyguDxTtSG9pZ5OXxLP4yADX8V2UWKMg                                   |
| ascii85             | Zd<KYS,S^k!m1n'`B-s:g0*LunLXYp!&a[UAJQ]8                                      |

For the sake of this example, I'm just going to choose hexadecimal:
```
b3d06b9d9bfe966e02ca0b83c53b521bda59e4e5f12cfe320035fc57651628c8
```

### String Example: Combination

Now we need to combine the **current time** with the **randomness** to make our _chrono random_ **GUID**.

There are a lot of different ways we could combine them.
Here is one of them:
```
<current time> ++ "_" ++ <randomness>
```

So, using our previous example, we could get:
```golang
"2022-03-30T02:35:46Z_b3d06b9d9bfe966e02ca0b83c53b521bda59e4e5f12cfe320035fc57651628c8"
```

This _could_ work as a _chrono random_ **GUID**, but it is space inefficient.

## Binary Example

We could be more space efficient if we combine the _current time_ and the _randomness_ together as binary.

### Binary Example: Binary Time Conventions

There are different ways of store **time** as binary.

How many **bits** do we use to store time?

What is the smallest **resolution** that can be represented?
A second?
A nanosecond?
A picosecond?
Etc?

What time does **zero** represent?

Etc.

These are just decisions that one needs to make. 
(Likely influenced by what the computers you have to deal with are capable of now, whatever future you are trying to future-proof for, plus likely what is familiar & easier for you, etc.)

### Binary Example: Unix Time

**Unix Time** is an example of a type of binary time representation that became popular with the rise of popularity of Unix & Linux.

Traditionally **unix time**:

* encoded time into **32-bits**,
* has a **resolution** of **seconds**,
* has **zero** represent **1970-01-01T00:00:00Z**.

Another implementation detail of **unix time** is that the **32-bit** representation is a **signed integer**.
Therefore —

Negative values are times _before_ the **zero** value (which corresponds to **1970-01-01T00:00:00Z**).

If we were to use **unix time** for our **binary time** for our **GUID**, to deal with its **year 2038 problem** (i.e., its **epochalypse**), we might make it to use **64-bits** (rather than **32-bits**).

(This won't get rid of the epochalypse. But it would instead move 32-bit unix time's epochalypse from Tuesday January 19th, 2038 at 03:14:07 UTC to some future date. And thus would make our **GUID**s be useful longer.)

### Binary Example: Randomness

For the **randomness**, we just need to pick how many bytes of randomness we want.

It needs to be _large-enough_.

For the sake of our example, we will just pick 64-bits of randomness.

### Binary Example: Chrono Random

So, given that we have chosen to use **64-bit** **unix time** for our **binary time**, and use **64-bits** (i.e., 8 bytes) of **randomness**, then —

If our **current time** was **Saturday April 30th at 02:35:46 GMT**, as 64-bit **unix time** this would be (in hexadecimal):
```
00 00 00 00 62 6C A0 82
```

And then maybe our 8 bytes of **randomness** would be:
```
b3 d0 6b 9d 9b fe 96 6e
```

And then we could combine them with the **current time** in the most-significant position, and the **randomness** in the least-significant position, to get:
```
00 00 00 00 62 6C A0 82 b3 d0 6b 9d 9b fe 96 6e  
\_____________________/ \_____________________/
           |                       |
      current time              randomness
```