# Unit Tests for uuid.Construct() ([UUID Guide](../../README.md))

by [Charles Iliya Krempeaux](http://changelog.ca/)

---

Now, write _unit tests_ for your `uuid.Construct()` function.

Here is some code to get you started:
```golang
func TestConstruct(t *testing.T) {

	tests := []struct{
		B0 byte
		B1 byte
		B2 byte
		B3 byte
		B4 byte
		B5 byte
		B6 byte
		B7 byte
		B8 byte
		B9 byte
		B10 byte
		B11 byte
		B12 byte
		B13 byte
		B15 byte
		B16 byte
		Expected [16]byte
	}{
		{
			B0:  0xea,
			B1:  0x35,
			B2:  0x42,
			B3:  0x7e,
			B4:  0xc3,
			B5:  0x9f,
			B6:  0x11,
			B7:  0xec,
			B8:  0x9d,
			B9:  0x64,
			B10: 0x02,
			B11: 0x42,
			B12: 0xac,
			B13: 0x12,
			B14: 0x00,
			B15: 0x02,
			Expected: [16]byte{0xea, 0x35, 0x42, 0x7e, 0xc3, 0x9f 0x11, 0xec, 0x9d, 0x64, 0x02, 0x42, 0xac, 0x12, 0x00, 0x02},
		},
		
		//@TODO: Add more test UUIDs
	}

	for testNumber, test := range tests {

		result := Construct(
			test.B0,
			test.B1,
			test.B2,
			test.B3,
			test.B4,
			test.B5,
			test.B6,
			test.B7,
			test.B8,
			test.B9,
			test.B10,
			test.B11,
			test.B12,
			test.B13,
			test.B14,
			test.B15,
		)
		actual := result.value
		
		expected := test.Expected
		
		if expected != actual {
			t.Errorf("For test #%d, the actual value is not what was expected.", testNumber)
			t.Logf("EXPECTED: %v", expected)
			t.Logf("ACTUAL:   %v", actual)
			continue
		}
	}
}
```

Complete the `//@TODO` in this code by adding 12 more test **UUID**s.
