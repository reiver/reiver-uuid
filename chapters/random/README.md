# Random ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

One **distributed** method of creating a **globally unique identifier** (**GUID**) is with **random numbers** chosen from a space that is large-enough.

**Version** `4` **UUID**s are these types of **globally unique identifiers** (**GUIDs**).
**Version** `4` **UUID**s are basically **121-bit** random numbers packaged into a **128-bits**.

If you are wonder why are **version** `4` **UUUD**s only **121-bit** random numbers, rather than **128-bit** random number —

The reason is that a **UUID** uses **4-bits** for the **UUID** **version**, and uses **3-bits** for the **UUID** **variant**.
So what you are left with for the random number is —

128-bits - 4-bits - 3-bits = 121-bits

What is kind of awkward about using **UUID**s as **random number** based **GUID**s is that — you have to split the random nunmber into 3 parts, because the **UUID** **version**, and the **UUID** **variant** are in the middle of the **UUID**.

