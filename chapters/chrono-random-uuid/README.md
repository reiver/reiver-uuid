# Chrono Random UUID ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

I already covered how to create a **chrono-random** **GUID** from scratch.

Now lets see how we could make **chrono-random** **UUID**s.

## UUID Version 4

You have already implemented **version 4** **UUID**s when you implemented your `uuid.Random()` function

Just to refresh — here are some example **version 4** **UUID**s expressed in their more human-readable canonical format (rather than their binary format):
                 ↓
* `f66c76f0-fcc3-49d8-91e1-49443826152d`
* `bc9253fe-94a9-449b-9a3c-0011314e9687`
* `015eeaed-a398-44d2-8ddc-2abe0114cfad`
* `9ccb9040-73a4-4563-bcb6-2bd672cbce13`

As you already know (because we already covered it), **UUID**s specify what **version** they are with the most-significant 4-bits of their 7th bytes.

You can easily see the **version** in the **UUID** canonical format by looking at this character:
```
           version
              ↓
f66c76f0-fcc3-49d8-91e1-49443826152d
bc9253fe-94a9-449b-9a3c-0011314e9687
015eeaed-a398-44d2-8ddc-2abe0114cfad
9ccb9040-73a4-4563-bcb6-2bd672cbce13
              ↑
           version
```

## UUID Variant

And **UUID**s specify their variant with the most-significant 3-bits of their 9th bytes.

This is difficult to see when looking at **UUID**s in their canonical format, but is easier to see if we switch to binary:
```
ed7ba470-8e54-465e-825c-99712043e01c
                   ⟱
           ┌───┬───┬───┬───┐
           │ 1 │ 0 │ 0 │ 0 │ = 8
           └───┴───┴───┴───┘
            \______/
               |
            variant
           ┌───┬───┐
           │ 1 │ 0 │ ⇝ RFC 4122
           └───┴───┘
```
```
f66c76f0-fcc3-49d8-91e1-49443826152d
                   ⟱
           ┌───┬───┬───┬───┐
           │ 1 │ 0 │ 0 │ 1 │ = 9
           └───┴───┴───┴───┘
            \______/
               |
            variant
           ┌───┬───┐
           │ 1 │ 0 │ ⇝ RFC 4122
           └───┴───┘
```
```
bc9253fe-94a9-449b-a93c-0011314e9687
                   ⟱
           ┌───┬───┬───┬───┐
           │ 1 │ 0 │ 1 │ 0 │ = a
           └───┴───┴───┴───┘
            \______/
               |
            variant
           ┌───┬───┐
           │ 1 │ 0 │ ⇝ RFC 4122
           └───┴───┘
```
```
9ccb9040-73a4-4563-bcb6-2bd672cbce13
                   ⟱
           ┌───┬───┬───┬───┐
           │ 1 │ 0 │ 1 │ 1 │ = b
           └───┴───┴───┴───┘
            \______/
               |
            variant
           ┌───┬───┐
           │ 1 │ 0 │ ⇝ RFC 4122
           └───┴───┘
```
