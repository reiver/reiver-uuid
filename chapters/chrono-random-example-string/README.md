# Example String Chrono Random GUID ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

This first example of a chrono-random **GUID** is a _string_ example.

This first example will NOT be a **UUID**.
But I think this non-**UUID** example will help make chrono-random **GUID**s make more sense if I show you it first (before we apply this technique to **UUID**s).

We need 2 things to construct a chrono-random **GUID**:

* the **current time**, and
* a **randomness**.

## Current Time

Let's say the **current time** is — **Saturday April 30th at 02:35:46 GMT**.

As a string, I could express this time in a number of different ways as a **string**.
Here are some examples:

| Format Name | Formatted Time                   |
|-------------|----------------------------------|
| GMT         | 2022-04-30T02:35:46Z             |
| ISO 8601    | 2022-04-30T02:35:46+00:00        |
| RFC 822     | Sat, 30 Apr 2022 02:35:46 +0000  |
| RFC 2822    | Saturday, 30-Apr-22 02:35:46 UTC |
| Unix Time   | 1651286146                       |

There are many other well-known time formats.
Plus, you could even create your own time format.
I'm sure you can imagine a lot of different ways of expressing this time.

For the sake of this example, I'm just going to choose _GMT_:
```
2022-04-30T02:35:46Z
```

(Of course, if you were to get the _current time_, it would be different for you.)

## Randomness

Now we need some randomness.

For the sake of this example, we will just get 32 random bytes:
```
b3 d0 6b 9d 9b fe 96 6e 02 ca 0b 83 c5 3b 52 1b 
da 59 e4 e5 f1 2c fe 32 00 35 fc 57 65 16 28 c8 
```

(Of course, if you were to get random-bytes, they will be different than these.)

With this too, we can express this in different ways as a **string**:

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

## Combination

Now we need to combine the **current time** with the **randomness** to make our _chrono random_ **GUID**.

There are a lot of different ways we could combine them.
Here is one of them:
```
<current time> ++ "_" ++ <randomness>
```

(If I was trying to future-proof this, I might also had **versioning** or **format** information to that somehow. But for the sake of keeping this example simple, I won't do that here.)

So, using our previous example _current-time_ and _randomness_, we could get:
```golang
"2022-03-30T02:35:46Z_b3d06b9d9bfe966e02ca0b83c53b521bda59e4e5f12cfe320035fc57651628c8"
```

## Do It Again

Let's see that again, but with a different _current-time_ and _randomness_.

Let's say our _current-time_ is:
```
2022-04-02T00:57:03Z
```

And let's say our _randomness_ is:
```
7cbc471e956bb9cc962fd8363fa56a2d3983288f0c5d00fe08e1a0c2e328181c
```

Then when we combine this we get our string-base chrono-random **GUID**:
```
2022-04-02T00:57:03Z_7cbc471e956bb9cc962fd8363fa56a2d3983288f0c5d00fe08e1a0c2e328181c
```

## String versus Binary

This technique & format _could_ work as a _chrono random_ **GUID**, but if we were to actually store it this was as a _string_ then it is space inefficient.

This _could_ be more space efficient if we instead used stored it in a binary format.
