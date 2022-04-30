# uuid.Construct() ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

Now you are going to create a function called `Construct` that will construct a `uuid.UUID` from 16 bytes:
```golang
package uuid

func Construct(
	b0 byte,
	b1 byte,
	b2 byte,
	b3 byte,
	b4 byte,
	b5 byte,
	b6 byte,
	b7 byte,
	b8 byte,
	b9 byte,
	b10 byte,
	b11 byte,
	b12 byte,
	b13 byte,
	b14 byte,
	b15 byte,
) UUID {
	//@TODO
}
```

(You are going to write the code for this, and replace the `//@TODO` with the actual implementation.)

So if I was to call:
```golang
value := uuid.Construct(0xed, 0x7b, 0xa4, 0x70, 0x8e, 0x54, 0x46, 0x5e, 0x82, 0x5c, 0x99, 0x71, 0x20, 0x43, 0xe0, 0x1c)
```

Then I expect this to construct the **UUID** `ed7ba470-8e54-465e-825c-99712043e01c`.

Which would mean that the `uuid.UUID.value` array would have a value of:
```golang
[16]byte{0xed, 0x7b, 0xa4, 0x70, 0x8e, 0x54, 0x46, 0x5e, 0x82, 0x5c, 0x99, 0x71, 0x20, 0x43, 0xe0, 0x1c}
