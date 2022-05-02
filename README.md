# GUIDE: uuid

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

This is a **guide** on **Universally Unique Identifiers** (**UUID**). I.e., things that look like these:

* `31905b9b-b1fa-4086-bcb9-bda8502a0958`
* `19077f38-5498-46a6-844d-f494086b8ca1`
* `e50c17c0-c9b0-11ec-9d64-0242ac120002`
* `49b1ca0e-d78f-55f3-8d58-197bac044ebb`
* `c8f0d7ec-9987-9f17-a7a4-a57f3318fb0e`

Although, don't confuse **UUID**s with **GUID**s (that were popularized by Microsoft).
They look the very very very similar, but aren't the same thing.

## Table of Contents

Overview

1. [Introduction](chapters/introduction/README.md)
2. [Usages](chapters/usages/README.md)
3. [Semiotics](chapters/semiotics/README.md)
4. [Unique ID](chapters/unique-id/README.md)
5. [Unique ID Examples](chapters/unique-id-examples/README.md)
6. [Centralized Unique ID](chapters/centralized-unique-id/README.md)
7. [Distributed Unique ID](chapters/distributed-unique-id/README.md)
8. [Bit Meaning](chapters/bit-meaing/README.md)
9. [Version](chapters/version/README.md)
10. [Variant](chapters/variant/README.md)
11. [Random](chapters/random/README.md)

Questions

12. [UUID Questions №1](chapters/questions-1/README.md)

Programming

13. Generating
14. [Git Repository](chapters/git-repository/README.md)
15. [Type](chapters/type/README.md)
16. [uuid.Construct()](chapters/function-construct/README.md)
17. [Unit Tests for uuid.Construct()](chapters/function-construct-unit-tests/README.md)
18. [fmt.Stringer](chapters/method-string/README.md)
19. [Unit Tests for fmt.Stringer](chapters/method-string-unit-tests/README.md)
20. [uuid.Random()](chapters/function-random/README.md)
21. [Unit Tests for uuid.Random()](chapters/function-random-unit-tests/README.md)

Project

22. [uuid Program](chapters/program-uuid/README.md)

Overview

23. [Chrono Random](chapters/chrono-random/README.md)
24. [Example String Chrono Random GUID](chapters/chrono-random-example-string/README.md)
25. [Example Binary Chrono Random GUID](chapters/chrono-random-example-binary/README.md)
26. [Chrono Random UUID](chapters/chrono-random-uuid/README.md)

Questions

27. [UUID Questions №2](chapters/questions-2/README.md)

Programming

28. [uuid.ChronoRandom()](chapters/function-chronorandom/README.md)
29. [Unit Tests for uuid.ChronoRandom()](chapters/function-chronorandom-unit-tests/README.md)

Project

30. uuid Program (chrono random)

Overview

31. [Binary](chapters/binary/README.md)

Programming

32. encoding.BinaryMarshaler
33. Unit Tests for encoding.BinaryMarshaler
34. encoding.BinaryUnmarshaler
35. Unit Tests for encoding.BinaryUnmarshaler

Project

36. uuid Program (binary)

Overview

37. Binary-To-Text Encoding

Programming

38. encoding.TextMarshaler
39. Unit Tests for encoding.Textmarshaler
40. encoding.TextUnmarshaler
41. Unit Tests for encoding.TextUnmarshaler

Project

42. JSON

Overview

43. Parsing

Programming

44. uuid.Parse()
45. Unit Tests for uuid.Parse()

Project

46. uuid Program

## Postamble

The purpose of this **guide** is to keep this **knowledge alive**.

To pass on an **understanding** sufficient for others, such as yourself, to be able to **implement** this themselves from-scratch — without making use of any previous implementations of it.

And to get others, such as yourself, to **implement** this themselves.

I think it is important for our **culture** that, as long as this is useful, not only does this (and other) knowledge stay as **living knowledge**, but that the ability to and practice of **re-creating it again**, without making use of any previous implementations of it, stays alive too.

To keep this alive, each generation needs to re-create it themselves, and use that implementation.

Create your own implementation of this.
Use your implementation.

This is how we can create a culture around this and other knowledge.
This is how we can create a tradition around this and other knowledge.
This is how we can create an institution around this and other knowledge.
