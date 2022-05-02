# Random ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

One **distributed** method of creating a **unique identifier** (**unique ID**) is with **random numbers** chosen from a space that is large-enough.

For example, randomly pick a number between `0` and `115,792,089,237,316,195,423,570,985,008,687,907,853,269,984,665,640,564,039,457,584,007,913,129,639,935`.
That number-range is huge!!

So, the important qualities is — the picking of the number has to be **random**, and the number-range has to be **huge**.

**RFC 4122** **Version** `4` **UUID**s are these types of **unique identifiers** (**unique IDs**).
**RFC 4122** **Version** `4` **UUID**s are basically **122-bit** random numbers packaged into a **128-bits**.

## 122-Bits?

If you are wondering why are **RFC 4122** **version** `4` **UUUD**s only **122-bit** random numbers, rather than **128-bit** random number —

The reason is that a **UUID** uses **4-bits** for the **UUID** **version**, and uses **2-bits** for the **UUID** **variant**.
So what you are left with for the random number is —

128-bits - 4-bits - 2-bits = 122-bits

With respect to these types of **distributed** random number **unique ID**s, a **UUID** wastes **6-bits**.

**UUID**s are doing something even worse than this, from a programming point of view, in that it makes packing the random numbers into the **UUID** awkward due to having to split the random nunmber into 3 parts, because of where **UUID** **version**, and the **UUID** **variant** are (in the middle of the **UUID**).

⚠️ Although I think **version** `4` **UUID**s are the _better_ types of **UUID**, I don't see why one would choose to use **UUID**s as their **unique ID**. Why waste 6-bits? Why have to split up the random number? What advantage does making a **UUID** give you (rather than just creating your own 64-bit, or 128-bit, or 256-bit, or whatever random number (and not bother with the whole **UUID** **version** and **UUID** **variant**)). But nevertheless, you will very likely come across **UUIDs**, and it would be to your benefit to understand them.
