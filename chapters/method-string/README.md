# fmt.Stringer ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

Now you are going to make your `uuid.UUID` type implement [fmt.Stringer](https://pkg.go.dev/fmt#Stringer).
```golang
package uuid 

func (receiver UUID) String() string {
	//@TODO
}
```

(You are going to write the code for this, and replace the `//@TODO` with the actual implementation.)

Your `.String()` method will return your **UUID** in the **canonical** format.

So, for example, if you created a **UUID** with a call like this:
```golang
value := uuid.Construct(0xed, 0x7b, 0xa4, 0x70, 0x8e, 0x54, 0x46, 0x5e, 0x82, 0x5c, 0x99, 0x71, 0x20, 0x43, 0xe0, 0x1c)
```

And thus your `uuid.UUID.value` field has a value of:
```golang
[16]byte{0xed, 0x7b, 0xa4, 0x70, 0x8e, 0x54, 0x46, 0x5e, 0x82, 0x5c, 0x99, 0x71, 0x20, 0x43, 0xe0, 0x1c}
```

Then your `String()` method would return:
```golang
"ed7ba470-8e54-465e-825c-99712043e01c"
