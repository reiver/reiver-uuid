# Unit Tests for uuid.Random() ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

Now you will write _unit tests_ for your `uuid.Random()` function, making sure that:

* `uuid.UUID.values[6] & 0xf0` is equal to `0x40`, and that 
* `uuid.UUID.values[8] & 0xc0` is equal to `0x80`,

… for any **UUID** that is returned from your `uuid.Random()` function.

Obviously this _unit test_ isn't going to test _all_ values returned from your `uuid.Random()` function. But you can test a fix number of samples from your `uuid.Random()` function. I.e., something like:
```golang
func TestRandom(t *testing.T) {

	const maxTests = 64

	for testNumber:=0; testNumber<maxTests; testNumber++ {
		var actual UUID = Random()
		
		//@TODO
	}
}
```
