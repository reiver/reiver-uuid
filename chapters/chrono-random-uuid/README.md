# Chrono Random UUID ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

You already covered how to create a **chrono-random** **GUID** from scratch.

Now lets see how we could make **chrono-random** **UUID**s.

## UUID Version 4

You have already implemented **version 4** **UUID**s when you implemented your `uuid.Random()` function

Just to refresh — here are some example **version 4** **UUID**s expressed in their more human-readable canonical format (rather than their binary format):
                 ↓
* `f66c76f0-fcc3-49d8-91e1-49443826152d`
* `bc9253fe-94a9-449b-9a3c-0011314e9687`
* `015eeaed-a398-44d2-8ddc-2abe0114cfad`

As you already know (because we already covered it), **UUID**s specify what **version** they are with the most-significant 4-bits of their 7th bytes.

You can easily see the **version** in the **UUID** canonical format by looking at this character:
```
           version
              ↓
f66c76f0-fcc3-49d8-91e1-49443826152d
bc9253fe-94a9-449b-9a3c-0011314e9687
015eeaed-a398-44d2-8ddc-2abe0114cfad
              ↑
           version
```

## UUID Variant

