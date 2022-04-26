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

| Type                | Value                                                                                                      |
|---------------------|------------------------------------------------------------------------------------------------------------|
| Canonical           | `ea35427e-c39f-11ec-9d64-0242ac120002`                                                                     |
| Hexadecimal Literal | `0xea35427ec39f11ec9d640242ac120002`                                                                       |
| Array of Bytes      | `[16]byte{0xea, 0x35, 0x42, 0x7e, 0xc3, 0x9f, 0x11, 0xec, 0x9d, 0x64, 0x02, 0x42, 0xac, 0x12, 0x00, 0x02}` |

The useful thing about the `ea35427e-c39f-11ec-9d64-0242ac120002` format is that it makes those **128-bits** of data recognizable as a **UUID**.

And most likely, when you see a **UUID**, you will see it in this type of format — `ea35427e-c39f-11ec-9d64-0242ac120002`

## Usages

People use UUIDs for all sorts of things.

But most of these uses involves a computer using a **UUID** as a type of globally unique **nickname** for something.

So, for example, imagine that on my phone I have an application that stores and manages my contacts. Maybe this is what is in my contact list:

| Family Name | Given Name | Additional Names | Phone Number |
|-------------|------------|------------------|--------------|
| Blow        | Joe        |                  | +16045555555 |
| Doe         | Jane       |                  | +17781234567 |
| Doe         | John       |                  | +17783456789 |
| Doe         | John       | Tiberius         | +12141212121 |

Internally the application secretly creates an _indentifier_ (_ID_) for each entry in the contact list.

The application could use a lot of different types of IDs for this.
But, an application might choose to use **UUID**s for its ID:


| ID                                   | Family Name | Given Name | Additional Names | Phone Number |
|--------------------------------------|-------------|------------|------------------|--------------|
| 9d49ff7d-186e-4bcb-8e75-534b8948b92f | Blow        | Joe        |                  | +16045555555 |
| d79d3ca5-49af-42a7-8565-477d2a91c95b | Doe         | Jane       |                  | +17781234567 |
| 29912c93-9671-424d-b633-b1bf2cd24c9c | Doe         | John       |                  | +17783456789 |
| 7a64d432-0ef8-45b4-9055-531f2b78b99e | Doe         | John       | Tiberius         | +12141212121 |

So, in this example, `9d49ff7d-186e-4bcb-8e75-534b8948b92f` is a nickname that the application uses for _Joe Blow_.
And `d79d3ca5-49af-42a7-8565-477d2a91c95b` is a nickname for _Jane Dow_.
Etc.

## Semiotics

If you are already aware of the jargon used in **semiotics** then, **UUID**s are **semiotic** **symbol**.

If that (stuff about **semiotics**) doesn't mean anything to you, then just ignore it, and keep on reading.

## GUID

There are other conventions for creating **globally unique identifiers** (**GUID**s) too, that are _not_ **UUID**s.
(You can even make up your own convention.) 
But in this **guide** we will focus on **UUID**s.

An **identifier** (**ID**) being **globally unique** means that it will be unique everywhere, and across time! That is strong property!

If you create a GUID today, and I create one tomorrow, they will be different.
If someone else creates one 100 years from now, it will also be different than both of the ones we created.
Etc.

⚠️ Note that I feel that there are better conventions for creating **GUID**s than **UUID**s (for reasons that will hopefully become more obvious as you work through this guide). But nevertheless, you will very likely come across **UUID**s, and it would be to your benefit to understand them.

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

Some bit ranges within the **128-bits** of a **UUID** have specific meanings. For example:

```
xxxxxxxx-xxxx-Mxxx-Nxxx-xxxxxxxxxxxx
```

The 4-bits of the `“M”` represents the **version** of the **UUID** that the **UUID** should be interpreted under.

And the most-significant 3-bits of the `“N”` represents the **variant** of the **UUID** that the **UUID** should be interpreted under.

## UUID Version

Let's look a little close at the **UUID version** bits.

For example, we migh have:

| UUID Version | Form                                  | Example                                 |
|--------------|---------------------------------------|-------------------------------------=---|
| Version 1    | `xxxxxxxx-xxxx-1xxx-Nxxx-xxxxxxxxxxxx` | `ea35427e-c39f-11ec-9d64-0242ac120002` |
| Version 4    | `xxxxxxxx-xxxx-4xxx-Nxxx-xxxxxxxxxxxx` | `5a768259-b599-4051-b647-714a5db21d0d` |

The version hexadecimal nibble is here:

```
              ↓
xxxxxxxx-xxxx-Mxxx-Nxxx-xxxxxxxxxxxx
xxxxxxxx-xxxx-1xxx-Nxxx-xxxxxxxxxxxx
xxxxxxxx-xxxx-4xxx-Nxxx-xxxxxxxxxxxx
ea35427e-c39f-11ec-9d64-0242ac120002
5a768259-b599-4051-b647-714a5db21d0d
9d345a19-98c6-4b36-8dbf-8c4cca4352f3
ed7ba470-8e54-465e-825c-99712043e01c
573e0100-1364-7a49-9b8f-6b3e35e8b3c4
              ↑
```

## UUID Variant

Now let's look a little close at the **UUID variant** bits.

The version hexadecimal nibble is here:

```
                   ↓
xxxxxxxx-xxxx-Mxxx-Nxxx-xxxxxxxxxxxx
xxxxxxxx-xxxx-1xxx-Nxxx-xxxxxxxxxxxx
xxxxxxxx-xxxx-4xxx-Nxxx-xxxxxxxxxxxx
ea35427e-c39f-11ec-9d64-0242ac120002
5a768259-b599-4051-b647-714a5db21d0d
9d345a19-98c6-4b36-8dbf-8c4cca4352f3
ed7ba470-8e54-465e-825c-99712043e01c
573e0100-1364-7a49-9b8f-6b3e35e8b3c4
                   ↑
```

But only part of that hexadecimal nibble are use for the **UUID variant**.

It can help to look at the “N”` nibble in binary to understand this better —
```
NNNx
```

Here is are some of the different types of variants that currently exist:

| Variant Name | Binary Value |
|--------------|--------------|
| RFC 4122     | 0b100        |
| Microsoft    | 0b110        |
| Future       | 0b111        |



