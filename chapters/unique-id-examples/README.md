# Unique ID Examples ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

Let's look at some examples of **unique ID**s to try to make some of this clearer.

## School ID

In some parts of the world, when you attend a school as a **student**, you are assigned a _special number_ that is often called something like your **student ID**.

Each new student that attends the school is given their own **student ID**.
And once a student is assigned a particular **student ID**, no other student will ever be given that **student ID**iss.

This **student ID** is a **unique ID**.

Let's look at an example school, to see what I mean.
Let's make up a school, for the sake of this example:
```
Fanstasy College
```

At Fantasy Collect, the staff at the school with assign to each new student a **student ID** made up of the following 4 pieces of information:
```
[YEAR] [MONTH] [CAMPUS] [SEQUENCE-NUMBER]
```

So, for example, if when the new student joined Fantasy College, we had:

* YEAR = `1995`
* MONTH = `09` (September)
* CAMPUS = `000`
* SEQUENCE-NUMBER = `08750`

I.e., this new student is the **8750th** student to join the school in **September** **1995** at campus **0000**.

Or in other words:
```
[YEAR] [MONTH] [CAMPUS] [SEQUENCE-NUMBER]
 1995    09      000        08750
```

Then could write the Fantasy Collect **student ID** for this new student as:
```
1995-09-000-08750
```

Or alternatively, could more compactly write it as:
```
19950900008750
```

What about the next new student to join Fantasy Collect at campus `000` in September 1995?
Well, that new student would be the 8751st student, and would be assigned the **student ID**:
```
19950900008751
```

Etc.

Here are some more example **student IDs**:
| Student ID     | Year | Month | Campus | Sequence Number |
|----------------|------|-------|--------|-----------------|
| 19950900008750 | 1995 | 09    | 000    | 08750           |
| 19950900008751 | 1995 | 09    | 000    | 08751           |
| 19950900005005 | 1995 | 09    | 000    | 05005           |
| 19960500012269 | 1996 | 05    | 000    | 12269           |
| 20000900118727 | 2000 | 09    | 001    | 18727           |
| 20220100421008 | 2022 | 01    | 004    | 21008           |


So, in the **domain** of **Fantast Collect**, the **student ID** is a **unique ID**.

## Database Primary-Key

Another example of a **locally** **unique identifier** (**unique ID**) is a _primary-key_ in a database table.

For example with the Postgres database, _primary-keys_ often have positive integer values such as — `1`, `2`, `3`, `4`, `5`, etc.
Within a single table these primary-key values are unique.
But other tables might also use those exact same alues for its own _primary-keys_.

For example, imagine you have a `users` table that uses positive integer **unique ID**s like so:

| ID  | username     |
|-----|--------------|
| `1` | joeblow      |
| `2` | janedoe      |
| `3` | johndoe      |
| `4` | hjsimpson    |
| `5` | brucebanner  |

And also, for example, imagine you have a `products` table that uses positive integer **unique ID**s like so:

| ID   | name     | price |
|------|----------|-------|
| `1`  | Skeletor | $14   |
| `2`  | Panthor  | $19   |
| `3`  | Moss-Man | $14   |
| `4`  | Webstor  | $14   |
| `5`  | Spikes   | $14   |

**ID** `1` is a nickname for `joeblow` in the `users` table, but **ID** `1` is also a nickname for `Skeletor` in the `products` table.

The same **ID**s are used in both tables, and have different means in each table.

If I just told you the **ID** is `5`, you wouldn't know if I'm referring to `brucebanner` (in the `users` table) or `Spikes` (in the `products` table), unless I also told you which table I was referring to.

So, in the **domain** of this particular `products` table, the **ID** primary-key is a **unique ID**.

## UUID

The intent of **UUID**s is that they are more broadly _unique_.

Let's look at what would happen if we instead used **UUID**s for the _primary-keys_

So, for example, imagine you have a `users` table that uses **UUID** as **unique ID**s like so:

| ID                                     | username     |
|----------------------------------------|--------------|
| `37bd2273-f442-4520-b2f7-7402eaab36c2` | joeblow      |
| `0b2bb6fb-27d4-49c6-8aad-304c015e1df5` | janedoe      |
| `a1192fd5-1fef-4054-8c44-5cf71e217283` | johndoe      |
| `84e60040-0f74-4a2a-9451-d068aa260c9d` | hjsimpson    |
| `8cff54ab-d888-4613-8363-dc264ff2937f` | brucebanner  |

And also, for example, imagine you have a `products` table that uses **UUID** as **unique IDs** like so:

| ID                                     | name     | price |
|----------------------------------------|----------|-------|
| `39bf9f7d-00ce-41e2-8645-75ffd4f65458` | Skeletor | $14   |
| `496bb0fe-2957-4d52-b48c-56e7fcb0c9e9` | Panthor  | $19   |
| `5b3a831c-9d64-42ad-82e4-fb734599bbda` | Moss-Man | $14   |
| `25197b99-655e-430c-9446-e991a874870f` | Webstor  | $14   |
| `dd001ac2-0c65-4b06-8a8a-8b98097b634f` | Spikes   | $14   |

If I just told you the ID is `dd001ac2-0c65-4b06-8a8a-8b98097b634f`, you wouldn't need me to tell you which table I was referring to, since it is _unique_ across all tables.

You would know, just with that **UUID**, that I was referring to the `products` table, and in particular, I was referring to `Spikes`.
