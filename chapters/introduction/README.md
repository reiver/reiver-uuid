# Introduction ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

**UUID**, short for **universally unique identifier**, is a popular convention for creating **unique identifiers** (**unique ID**s).

(If you aren't sure what a **unique identifier** (**unique ID**) is yet, we will go into that more later.)

Often, when **UUID**s are written, they look like these:

* `ea35427e-c39f-11ec-9d64-0242ac120002`
* `5a768259-b599-4051-b647-714a5db21d0d`
* `9d345a19-98c6-4b36-8dbf-8c4cca4352f3`
* `ed7ba470-8e54-465e-825c-99712043e01c`
* `573e0100-1364-7a49-9b8f-6b3e35e8b3c4`

I.e., a sequence of 32 hexadecimal symbols split-up by hyphens at certain places.

## 128-Bits

Each of these **UUID**s is really just **128-bits** of data.

Which, if you are dealing with 8-bit bytes (as most computers have nowadays) then ⁠— each of these **UUID**s is really just **16 bytes** of data.

You could equally write a **UUID** such as `ea35427e-c39f-11ec-9d64-0242ac120002` as the follows:

| Type                | Value                                                                                                                              |
|---------------------|------------------------------------------------------------------------------------------------------------------------------------|
| Canonical           | `ea35427e-c39f-11ec-9d64-0242ac120002`                                                                                             |
| Hexadecimal Literal | `0xea35427ec39f11ec9d640242ac120002`                                                                                               |
| Hexadecimal         | `ea35427ec39f11ec9d640242ac120002`                                                                                                 |
| Array of Bytes      | `[16]byte{0xea, 0x35, 0x42, 0x7e, 0xc3, 0x9f, 0x11, 0xec, 0x9d, 0x64, 0x02, 0x42, 0xac, 0x12, 0x00, 0x02}`                         |
| Binary              | `11101010001101010100001001111110110000111001111100010001111011001001110101100100000000100100001010101100000100100000000000000010` |
| base32              | `5I2UE7WDT4I6ZHLEAJBKYEQAAI======`                                                                                                 |
| bas64               | `6jVCfsOfEeydZAJCrBIAAg==`                                                                                                         |
| base64url           | `6jVCfsOfEeydZAJCrBIAAg`                                                                                                           |
| ascii85             | `l8:nW_k.P-SR_dgX:bL7`                                                                                                             |

The useful thing about the (**canonical**) `ea35427e-c39f-11ec-9d64-0242ac120002` format is that it makes those **128-bits** of data recognizable as a **UUID**.

And most likely, when you see a **UUID**, you will see it in this type of format — `ea35427e-c39f-11ec-9d64-0242ac120002`

## Storage

Although hopefully when a **UUID** is being stored — it is being story efficiently as **128-bits** = **16 bytes** of data (rather than a string of its **canonical** form inefficiently taking up at least 36 bytes).

So, stored as:
```
ea 35 42 7e c3 9f 11 ec
9d 64 02 42 ac 12 00 02
```

Rather than (in ASCII / Unicode) as:
```
65 61 33 35 34 32 37 65
2d 63 33 39 66 2d 31 31
65 63 2d 39 64 36 34 2d
30 32 34 32 61 63 31 32
30 30 30 32
```

(Hopefully it is obvious that the latter is just the ASCII / Unicode UTF-8 encoding of the canonical form string.)
