# uuid Program ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

You are going to use the `uuid` package you just created to create a new program.

You are going to create a program (also) named `uuid`.

## Requirements

This new program you are going to create will output the **canonical** form of a **UUID** created from your ``uuid.Random()`` function using `fmt.Println()`.

So, for example, if I were at the shell, I might run it like:
```
$ ./uuid
```

And it might output:
```
99b7f609-26e3-47e4-8fb6-ec3acbc6e61e
```

Of course, this is a randomly generated **UUID**, so each time you run your new `uuid` program it should return a different **UUID**.

```
$ ./uuid
7253687d-c85b-4b03-aca0-ee487f4e2cef

$
```

## Git Repository

You will create a new git repository for this called `uuid`

So, for example, if you were on `github.com` and your username was `joeblow`, then you new git respository would be at:
```
https://github.com/jowblow/uuid
```

(Luckily the name of the repository for your package is `go-uuid` and not `uuid`, so there will be no conflict.)
