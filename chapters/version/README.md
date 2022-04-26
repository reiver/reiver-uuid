# Version ([UUID Guide](../../README.md))

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

The 4-bits of the `“M”` represents the **version** of the **UUID** that the **UUID** should be interpreted under.

So, for example, consider this **UUID**:
```
            version
              ↓
4ffed962-adf6-4eef-931d-8d95b798c080
                   ↑
                variant
``` 

The **version** of this **UUID** is `4`.

Now, also for example, consider this **UUID**:
```
            version
              ↓
5fd2c9d6-c52e-11ec-9d64-0242ac120002
                   ↑
                variant
```

The **version** of this **UUID** is `1`.

Let's look a little closer at the **UUID version** bits.

For example, we migh have:

| UUID Version | Format                                 | Example                                |
|--------------|----------------------------------------|----------------------------------------|
| Version 1    | `xxxxxxxx-xxxx-1xxx-Nxxx-xxxxxxxxxxxx` | `ea35427e-c39f-11ec-9d64-0242ac120002` |
| Version 4    | `xxxxxxxx-xxxx-4xxx-Nxxx-xxxxxxxxxxxx` | `5a768259-b599-4051-b647-714a5db21d0d` |

The version hexadecimal nibble is here:

```
            version
              ↓
xxxxxxxx-xxxx-Mxxx-Nxxx-xxxxxxxxxxxx
              ↑
            version


            version
              ↓
xxxxxxxx-xxxx-1xxx-Nxxx-xxxxxxxxxxxx
xxxxxxxx-xxxx-4xxx-Nxxx-xxxxxxxxxxxx
              ↑
            version

            version
              ↓
ea35427e-c39f-11ec-9d64-0242ac120002
5a768259-b599-4051-b647-714a5db21d0d
9d345a19-98c6-4b36-8dbf-8c4cca4352f3
ed7ba470-8e54-465e-825c-99712043e01c
573e0100-1364-7a49-9b8f-6b3e35e8b3c4
              ↑
            version
```

So, for example, here is the version more explictly stated for each of these sample **UUID**s:

| UUID                                   | UUID Version |
|----------------------------------------|--------------|
| `xxxxxxxx-xxxx-1xxx-Nxxx-xxxxxxxxxxxx` | `1`          |
| `xxxxxxxx-xxxx-4xxx-Nxxx-xxxxxxxxxxxx` | `4`          |
| `ea35427e-c39f-11ec-9d64-0242ac120002` | `1`          |
| `5a768259-b599-4051-b647-714a5db21d0d` | `4`          |
| `9d345a19-98c6-4b36-8dbf-8c4cca4352f3` | `4`          |
| `ed7ba470-8e54-465e-825c-99712043e01c` | `4`          |
| `573e0100-1364-7a49-9b8f-6b3e35e8b3c4` | `7`          |

## Version 4

Nowadays the most popular **version** of **UUID** to create yourself is **UUID** **version** `4` (with a **UUID** **variant** of `RFC 4122` (`100`)).

Why this is the case will hopefully make more sense as your progress through this **guide**.
