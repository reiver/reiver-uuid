# Type ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

You are going to create a type that represents a **UUID**.

And you are going to store the **UUID** efficiently as binary!

(This, storing the **UUID** as binary, is imporant!)

So:
```golang
package uuid

type UUID struct {
	value [16]byte
}
```

This means that, for example, the **UUID** `56676d4d-2cb5-4b69-a141-9dd6922b74b0` (would not be stored as a `string` that looks like that, but instead) would be stored in `value` as:
```golang
[]byte{0x56, 0x67, 0x6d, 0x4d, 0x2c, 0xb5, 0x4b, 0x69, 0xa1, 0x41, 0x9d, 0xd6, 0x92, 0x2b, 0x74, 0xb0}
```
