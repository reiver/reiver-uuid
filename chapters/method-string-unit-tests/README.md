# Unit Tests for fmt.Stringer ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

Write _unit tests_ for your `uuid.UUID.String()` method.

Here is some code to get you started:
```golang
func TestUUID_String(t *testing.T) {

	tests := []struct{
		UUID uuid.UUID
		Expected string
	}{
		{
			UUID: uuid.Construct(0xed, 0x7b, 0xa4, 0x70, 0x8e, 0x54, 0x46, 0x5e, 0x82, 0x5c, 0x99, 0x71, 0x20, 0x43, 0xe0, 0x1c),
			Expected: "ed7ba470-8e54-465e-825c-99712043e01c"
		},
		
		//@TODO: Add more test UUIDs
	}

	for testNumber, test := range tests {
		actual := test.UUID.String()
		expected := test.Expected
		
		if expected != actual {
			t.Errorf("For test #%d, is actual value is not what was expected.", testNumber)
			t.Logf("EXPECTED: %s", expected)
			t.Logf("ACTUAL:   %s", actual)
			continue
		}
	}
}
```

Complete the `//@TODO` in this code by adding 12 more test **UUID**s.
