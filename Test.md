```go
func TestReverseBytes(t *testing.T) {
	// Test case 1: Even-length input
	input1 := []byte{1, 2, 3, 4}
	expected1 := []byte{4, 3, 2, 1}
	result1 := reverseBytes(input1)

	if !reflect.DeepEqual(result1, expected1) {
		t.Errorf("Expected %v, but got %v", expected1, result1)
	}

	// Test case 2: Odd-length input
	input2 := []byte{5, 6, 7, 8, 9}
	expected2 := []byte{9, 8, 7, 6, 5}
	result2 := reverseBytes(input2)

	if !reflect.DeepEqual(result2, expected2) {
		t.Errorf("Expected %v, but got %v", expected2, result2)
	}

	// Test case 3: Empty input
	input3 := []byte{}
	expected3 := []byte{}
	result3 := reverseBytes(input3)

	if !reflect.DeepEqual(result3, expected3) {
		t.Errorf("Expected %v, but got %v", expected3, result3)
	}
}
```
