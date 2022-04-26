# Introduction ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

**UUID** (short for **universally unique identifier**) is a popular convention for creating **globally unique identifiers** (**GUID**s).

(If you aren't sure what a **globally unique identifier** (**GUID**) is yet, we will go into that more later.)

Often, when **UUID**s are written, they look like these:

* `ea35427e-c39f-11ec-9d64-0242ac120002`
* `5a768259-b599-4051-b647-714a5db21d0d`
* `9d345a19-98c6-4b36-8dbf-8c4cca4352f3`
* `ed7ba470-8e54-465e-825c-99712043e01c`
* `573e0100-1364-7a49-9b8f-6b3e35e8b3c4`

Each of these **UUID**s is really just **128-bits** of data.

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

The useful thing about the (canonical) `ea35427e-c39f-11ec-9d64-0242ac120002` format is that it makes those **128-bits** of data recognizable as a **UUID**.

And most likely, when you see a **UUID**, you will see it in this type of format — `ea35427e-c39f-11ec-9d64-0242ac120002`

## LUID

A **globally unique identifier** (**GUID**) would be contrasted against a **locally unique identifier** (**LUID**).

An example of a **locally unique identifier** is a _primary-key_ in a database table. For example in Postgres _primary-keys_ often have positive integer values such as — `1`, `2`, `3`, `4`, `5`, etc. Within a single table these are unique. But other tables might also use those exact same alues for its own _primary-keys_.

For example, imagine you have a `users` table that uses positive integer **LUID**s like so:

| ID  | username     |
|-----|--------------|
| `1` | joeblow      |
| `2` | janedoe      |
| `3` | johndoe      |
| `4` | hjsimpson    |
| `5` | brucebanner  |

And also, for example, imagine you have a `products` table that uses positive integer **LUIDs** like so:

| ID   | name     | price |
|------|----------|-------|
| `1`  | Skeletor | $14   |
| `2`  | Panthor  | $19   |
| `3`  | Moss-Man | $14   |
| `4`  | Webstor  | $14   |
| `5`  | Spikes   | $14   |

**ID** `1` is a nickname for `joeblow` in the `users` table, but **ID** `1` is also a nickname for `Skeletor` in the `products` table.

The same **ID**s are used in both tables, and have different means in each table.

If I just told you the **ID** is `5`, you wouldn't know if I'm referring to `brucebanner` or `Spikes`, unless I also told you which table I was referring to.

**UUID**s are NOT **locally unique identifiers** (**LUID**), they are **globally unique identifiers** (**GUID**).
If they were used for _primary-keys_ of database tables, they would be unique everywhere, with every database in the universe, and across time.

So, for example, imagine you have a `users` table that uses **UUID** **GUID**s like so:

| ID                                     | username     |
|----------------------------------------|--------------|
| `37bd2273-f442-4520-b2f7-7402eaab36c2` | joeblow      |
| `0b2bb6fb-27d4-49c6-8aad-304c015e1df5` | janedoe      |
| `a1192fd5-1fef-4054-8c44-5cf71e217283` | johndoe      |
| `84e60040-0f74-4a2a-9451-d068aa260c9d` | hjsimpson    |
| `8cff54ab-d888-4613-8363-dc264ff2937f` | brucebanner  |

And also, for example, imagine you have a `products` table that uses **UUID** **GUIDs** like so:

| ID                                     | name     | price |
|----------------------------------------|----------|-------|
| `39bf9f7d-00ce-41e2-8645-75ffd4f65458` | Skeletor | $14   |
| `496bb0fe-2957-4d52-b48c-56e7fcb0c9e9` | Panthor  | $19   |
| `5b3a831c-9d64-42ad-82e4-fb734599bbda` | Moss-Man | $14   |
| `25197b99-655e-430c-9446-e991a874870f` | Webstor  | $14   |
| `dd001ac2-0c65-4b06-8a8a-8b98097b634f` | Spikes   | $14   |

If I just told you the ID is `dd001ac2-0c65-4b06-8a8a-8b98097b634f`, you wouldn't need me to tell you which table I was referring to, since it is a **GUID**. You would know just with that information that I was referring to the `products` table, and in particular, I was referring to `Spikes`.

**UUID**s are **GUID**s (_not_ **LUID**s).

## Distributed GUID versus Centralized GUID

There are two main strategies for creating a **GUID**:

* distributed, and
* centralized.

**UUID**s are a set of strategies for creating distributed **GUID**s.

## Meaning

Let's look a little closer at **UUID**s.

A **UUID** is 128-bits of data — do any of those bits have special meanings? The answer is — yes.
Some bit ranges within the **128-bits** of a **UUID** have specific meanings. For example:

```
xxxxxxxx-xxxx-Mxxx-Nxxx-xxxxxxxxxxxx
```

The 4-bits of the `“M”` represents the **version** of the **UUID** that the **UUID** should be interpreted under.

And the most-significant 3-bits of the `“N”` represents the **variant** of the **UUID** that the **UUID** should be interpreted under.

So, for example, consider this **UUID**L
```
            version
              ↓
4ffed962-adf6-4eef-931d-8d95b798c080
                   ↑
                variant
``` 

The version is **UUID** **version** is `4`.

And the **UUID** **variant** is `8`.
(Why the **UUID** **variant** is `8` rather than `9` in this example will make more sense later, when we look at the **UUID** **variant** more closely.)

## Next

Now let's dig into the **UUID** **version** and **UUID** **variant** a bit more.
