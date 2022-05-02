# Unique ID Examples ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

Let's look at some examples of **unique ID**s to try to make some of this clearer.

## Database Primary-Key

An example of a **locally** **unique identifier** (**unique ID**) is a _primary-key_ in a database table.

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
