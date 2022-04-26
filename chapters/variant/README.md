# Variant ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

A **UUID** is 128-bits of data — and some of the bits in a **UUID** have special meanings.
In particular, some bit ranges within the **128-bits** of a **UUID** have specific meanings. For example:

```
            version
              ↓
xxxxxxxx-xxxx-Mxxx-Nxxx-xxxxxxxxxxxx
                   ↑
                variant
```

The most-significant 3-bits of the `“N”` represents the **variant** of the **UUID** that the **UUID** should be interpreted under.

So, for example, consider this **UUID**:
```
            version
              ↓
4ffed962-adf6-4eef-931d-8d95b798c080
                   ↑
                variant
``` 

The **variant** of this **UUID** is (in binary) `100`.

It is (in binary) `100` because of (hexadecinal) `9` is (in binary) `1001`, and the most-significant 3-bits of `1001` is `100`.

Let's look a little closer at the **UUID variant** bits.

The **variant** hexadecimal nibble is here:

```
                variant
                   ↓
xxxxxxxx-xxxx-Mxxx-Nxxx-xxxxxxxxxxxx
                   ↑
                variant

                variant
                   ↓
xxxxxxxx-xxxx-1xxx-Nxxx-xxxxxxxxxxxx
xxxxxxxx-xxxx-4xxx-Nxxx-xxxxxxxxxxxx
                   ↑
                variant

                variant
                   ↓
ea35427e-c39f-11ec-9d64-0242ac120002
5a768259-b599-4051-b647-714a5db21d0d
9d345a19-98c6-4b36-8dbf-8c4cca4352f3
ed7ba470-8e54-465e-825c-99712043e01c
573e0100-1364-7a49-9b8f-6b3e35e8b3c4
                   ↑
                variant
```

But only part of that hexadecimal nibble are use for the **UUID variant**.

Only the most significant 3-bits of the **UUID variant** nibble is relevant.

Let's make this more explicit.

| Nibble (Hexadecimal) | Nibble (Binary) | Variant (Binary) | Variant   |
|----------------------|-----------------|------------------|-----------|
| `0`                  | `0000`          | `000`            |           |
| `1`                  | `0001`          | `000`            |           |
| `2`                  | `0010`          | `001`            |           |
| `3`                  | `0011`          | `001`            |           |
| `4`                  | `0100`          | `010`            |           |
| `5`                  | `0101`          | `010`            |           |
| `6`                  | `0110`          | `011`            |           |
| `7`                  | `0111`          | `011`            |           |
| `8`                  | `1000`          | `100`            | RFC 4122  |
| `9`                  | `1001`          | `100`            | RFC 4122  |
| `a`                  | `1010`          | `101`            |           |
| `b`                  | `1011`          | `101`            |           |
| `c`                  | `1100`          | `110`            | Microsoft |
| `d`                  | `1101`          | `110`            | Microsoft |
| `e`                  | `1110`          | `111`            | Future    |
| `f`                  | `1111`          | `111`            | Future    |


Notice that the “**Variant (Binary)** ” column is just the first 3-bits of the “**Nibble (Binary)**” coloumn. I.e.,:

```
NNNx
```

Here is are some of the different types of variants that currently exist:

| Variant Name | Binary Value |
|--------------|--------------|
| RFC 4122     | `100`        |
| Microsoft    | `110`        |
| Future       | `111`        |
