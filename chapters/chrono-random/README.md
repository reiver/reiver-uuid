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

## Example Chrono Random GUIDs

Let's look at an examples of a chrono-random **GUID**s try to make all this clearer.
