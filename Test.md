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


type mockContext struct {
}

func (m *mockContext) GetStatusChange(readers []scard.ReaderState, timeout int) error {
	// Add your mock implementation here
	return nil
}

func TestWaitUntilCardPresent(t *testing.T) {
	// Mocked scard.Context for testing
	mockCtx := &mockContext{}

	// Test case 1: Card present in the first reader
	readers1 := []string{"Reader1", "Reader2"}
	result, err := waitUntilCardPresent(mockCtx, readers1)
	if err != nil {
		t.Errorf("Unexpected error: %v", err)
	}
	if result != 0 {
		t.Errorf("Expected result 0, got %d", result)
	}

	// Test case 2: Card present in the second reader
	readers2 := []string{"Reader2", "Reader1"}
	result, err = waitUntilCardPresent(mockCtx, readers2)
	if err != nil {
		t.Errorf("Unexpected error: %v", err)
	}
	if result != 1 {
		t.Errorf("Expected result 1, got %d", result)
	}

	// Add more test cases as needed

	// Test case for error scenario
	// mockCtxWithError := &mockContextWithError{} // Implement a mock with an error for GetStatusChange
	// result, err = waitUntilCardPresent(mockCtxWithError, readers1)
	// if err == nil {
	// 	t.Error("Expected an error, but got nil")
	// }

	// You can add more test cases to cover edge cases and error scenarios
}
```
