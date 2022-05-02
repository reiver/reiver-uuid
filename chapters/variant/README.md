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

How many bits the **variant** is depends on what the  value of the **variant** is.
The **variant** can either be 1, 2, or 3 most-significant bits of the `“N”` nibble.

The following table illustrates the **variant** more:

| Nibble | Binary | Variant (Binary) | # of Bits | Variant (Name) |
|--------|--------|------------------|-----------|----------------|
| 0      | `0000` | `0`              | 1         | Apollo NCA     |
| 1      | `0001` | `0`              | 1         | Apollo NCA     |
| 2      | `0010` | `0`              | 1         | Apollo NCA     |
| 3      | `0011` | `0`              | 1         | Apollo NCA     |
| 4      | `0100` | `0`              | 1         | Apollo NCA     |
| 5      | `0101` | `0`              | 1         | Apollo NCA     |
| 6      | `0110` | `0`              | 1         | Apollo NCA     |
| 7      | `0111` | `0`              | 1         | Apollo NCA     |
| 8      | `1000` | `10`             | 2         | **RFC 4122**   |
| 9      | `1001` | `10`             | 2         | **RFC 4122**   |
| a      | `1010` | `10`             | 2         | **RFC 4122**   |
| b      | `1011` | `10`             | 2         | **RFC 4122**   |
| c      | `1100` | `110`            | 3         | Microsoft      |
| d      | `1101` | `110`            | 3         | Microsoft      |
| e      | `1110` | `111`            | 3         | Future         |
| f      | `1111` | `111`            | 3         | Future         |

(“Apollo NCA” = “Apollo Network Computer Architecture”)

So, said another way, the number of bits that **variant** takes up is given by this table:
| Variant (Name) | # of Bits |
|----------------|-----------|
| Apollo NCS     | 1         |
| **RFC 4122**   | 2         |
| Microsoft      | 3         |
| Future         | 3         |

(Right now, we are mostly going to focus on **RFC 4122** **UUID**s, so the **variant** will take up 2-bits.)

## Example

So, for example, consider this **UUID**:
```
            version
              ↓
4ffed962-adf6-4eef-931d-8d95b798c080
                   ↑
                variant
``` 

The nibble the **variant** is encoded into is hexadecimal `9`.

As binary hexadecimal `9` is `1001`.

That matches an **RFC 4122** 2-bit **variant**:
```
  1001
  ↑↑
variant

```

## More Examples

Let's look at more examples:
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
