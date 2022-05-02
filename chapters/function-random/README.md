# uuid.Random() ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

Now you are going to create a function that creates a random **UUID**:
```golang
package uuid

func Random() UUID {
	//@TODO
}
```

(You are going to write the code for this, and replace the `//@TODO` with the actual implementation.)

Your implementation should do the following:

№1: set the values of each byte in `uuid.UUID.value` randomly,

№2: set the most-significant 4-bits of `uuid.UUID.value[6]` to `0b0100`,

№3: set the most-significant 2-bits of `uuid.UUID.value[8]` to `0b10`
