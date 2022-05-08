# Unique ID ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

A **unique identifier** (**unique ID**) is an **identifier** (**ID**) that is **unique** across some (implicitly or explicitly defined) **domain**.

Let's provide some examples to make all that jargon make more sense.

## Example: 

In some parts of the world, when you attend a school, you are assigned a special number often called something like your **student ID**.

Let's say that in our example school, the way they generate a new _unique_ **student ID** for a new student is:
```
[YEAR] [MONTH] [CAMPUS] [SEQUENCE-NUMBER]
```

So, for example, if:

* YEAR = `1995`
* MONTH = `09` (September)
* CAMPUS = `000`
* SEQUENCE-NUMBER = `08750`

Then this new student is the **8750th** student to join the school in **September** **1995** at campus **0000**.

Or in other words:
```
[YEAR] [MONTH] [CAMPUS] [SEQUENCE-NUMBER]
 1995    09      000        08750
```

This **student ID** might be written as: `1995-09-000-08750`.

And might even be more compactly written as: `19950900008750`

So, also for example, the next student to join in September 1995 at campus 000, would be the 8751st student, and would be the **student ID**: `19950900008751`.

Etc.

Here are some more example **student IDs**:
| Student ID     | Year | Month | Campus | Sequence Number |
|----------------|------|-------|--------|-----------------|
| 19950900008750 | 1995 | 09    | 000    | 08750           |
| 19950900008751 | 1995 | 09    | 000    | 08751           |
| 19950900005005 | 1995 | 09    | 000    | 05005           |
| 19960500012269 | 1996 | 05    | 000    | 12269           |
| 20220900421008 | 2022 | 09    | 004    | 21008           |


Each new student that attends the school is given their own **student ID**.
And once a student is assigned a particular **student ID**, no other student will ever be given that **student ID**iss.

So, the **domain** in this example is **this school**.
The **unique ID** is the **student ID**.
And thus the **student ID** is **unique** in **this school**.

## Example

Imagine you created a database.
And in that database was a table.

It doesn't really matter than the table stores, but for the sake of the example, lets say it is a table named `toys`.

The domain could be just within a single database table within a specific database.

So, in our example, the _domain_ would be our `toys` table.
#######

The domain could be the universe of all **IDs** that have ever been created, and will ever be created, across time, and across the unverse!
I.e., —
If you create this type of **ID** today, and I create this type of **ID** tomorrow, they will be different.
If someone else creates this type of **ID** 100 years from now, it will also be different than both of the **ID**s we each created.
Etc.

## UUID

**UUID** is an attempt at creating a set of conventions for creating **unique identifiers** (**ID**s) that are unique globally and perhaps even intra-solar'ly, and at the scale of thousands of years.

There are other conventions **unique identifiers** (**unique ID**s) of this scale too, that are _not_ **UUID**s.
(You can even make up your own convention.) 
But in this **guide** we will focus on **UUID**s.


⚠️ Note that I feel that there are better conventions for creating **unique ID**s (of this scale) than **UUID**s (for reasons that will hopefully become more obvious as you work through this guide). But nevertheless, you will very likely come across **UUID**s, and it would be to your benefit to understand them.
