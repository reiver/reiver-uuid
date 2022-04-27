# Random ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

One **distributed** method of creating a **globally unique identifier** (**GUID**) is with **random numbers** chosen from a space that is large-enough.

For example, randomly pick a number between `0` and `115,792,089,237,316,195,423,570,985,008,687,907,853,269,984,665,640,564,039,457,584,007,913,129,639,935`. That number range is huge!!

So, the important qualities is — the picking of the number has to be **random**, and the number range has to be **huge**.

**Version** `4` **UUID**s are these types of **globally unique identifiers** (**GUIDs**).
**Version** `4` **UUID**s are basically **121-bit** random numbers packaged into a **128-bits**.

If you are wondering why are **version** `4` **UUUD**s only **121-bit** random numbers, rather than **128-bit** random number —

The reason is that a **UUID** uses **4-bits** for the **UUID** **version**, and uses **3-bits** for the **UUID** **variant**.
So what you are left with for the random number is —

128-bits - 4-bits - 3-bits = 121-bits

With respect to these types of **distributed** random number **GUID**s, a **UUID** wasted **7-bits**.

**UUID**s are do something even worse than this, from a programming point of view, in makes putting the random numbser into the **UUID**s awkward as **random number** based **GUID**s because you have to split the random nunmber into 3 parts, because the **UUID** **version**, and the **UUID** **variant** are in the middle of the **UUID**.

⚠️ Although I think **version** `4` **UUID**s are the _better_ types of **UUID**, I don't see why one would choose to use **UUID**s as their **GUID**. Why waste 7-bits? Why have to split up the random number? What advantage does making it a **UUID** give you (rather than just creating your own 64-bit, or 128-bit, or 256-bit, or whatever random number (and not bother with the whole **UUID** **version** and **UUID** **variant**)). But nevertheless, you will very likely come across **UUIDs**, and it would be to your benefit to understand them.

