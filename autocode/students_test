package coverage

import (
	"os"
	"testing"
	"time"
	"reflect"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW
func TestPeople_Len(t *testing.T) {
	var people = People{
		{
			firstName: "Chrissy",
			lastName:  "Costanza",
			birthDay:  time.Date(1995, time.August, 23, 0, 0, 0, 0, time.UTC),
		},
		{
			firstName: "Audra",
			lastName:  "Miller",
			birthDay:  time.Date(2001, time.July, 11, 0, 0, 0, 0, time.UTC),
		},
		{
			firstName: "Jada",
			lastName:  "Facer",
			birthDay:  time.Date(2001, time.March, 18, 0, 0, 0, 0, time.UTC),
		},
		{
			firstName: "Violet",
			lastName:  "Orlandi",
			birthDay:  time.Date(1995, time.February, 17, 0, 0, 0, 0, time.UTC),
		},
	}

	var result = people.Len()

	if result != 4 {
		t.Errorf("the expected length is 4, but actual is %d", result)
	}
}

func TestPeople_Less(t *testing.T) {
	var people = People{
		{
			lastName: "Costanza",
		},
		{
			lastName: "Facer",
		},
		{
			firstName: "Chrissy",
		},
		{
			firstName: "Audra",
		},
		{
			birthDay: time.Date(2001, time.March, 18, 0, 0, 0, 0, time.UTC),
		},
		{
			birthDay: time.Date(1995, time.February, 17, 0, 0, 0, 0, time.UTC),
		},
	}

	var testData = map[string]struct {
		i        int
		j        int
		Expected bool
	}{
		"first is less than second (compare by lastName)": {
			i:        0,
			j:        1,
			Expected: true,
		},
		"first is less than second (compare by firstName)": {
			i:        2,
			j:        3,
			Expected: false,
		},
		"first is less than second (compare by birthDay)": {
			i:        4,
			j:        5,
			Expected: true,
		},
	}

	for name, testCase := range testData {
		t.Run(name, func(t *testing.T) {
			var result = people.Less(testCase.i, testCase.j)

			if result != testCase.Expected {
				t.Errorf("%v, expected %v", name, testCase.Expected)
			}
		})
	}
}

func TestPeople_Swap(t *testing.T) {
	var people = People{
		{
			firstName: "Chrissy",
			lastName:  "Costanza",
			birthDay:  time.Date(1995, time.August, 23, 0, 0, 0, 0, time.UTC),
		},
		{
			firstName: "Audra",
			lastName:  "Miller",
			birthDay:  time.Date(2001, time.July, 11, 0, 0, 0, 0, time.UTC),
		},
		{
			firstName: "Jada",
			lastName:  "Facer",
			birthDay:  time.Date(2001, time.March, 18, 0, 0, 0, 0, time.UTC),
		},
		{
			firstName: "Violet",
			lastName:  "Orlandi",
			birthDay:  time.Date(1995, time.February, 17, 0, 0, 0, 0, time.UTC),
		},
	}

	var firstPesrsonBeforeSwap = people[0]
	var secondPesrsonBeforeSwap = people[2]

	people.Swap(0, 2)

	var firstPesrsonAfterSwap = people[0]
	var secondPesrsonAfterSwap = people[2]

	if !reflect.DeepEqual(firstPesrsonBeforeSwap, secondPesrsonAfterSwap) {
		t.Error("error during swap for first argument")

	}

	if !reflect.DeepEqual(secondPesrsonBeforeSwap, firstPesrsonAfterSwap) {
		t.Error("error during swap for second argument")
	}
}

func TestMatrix_New(t *testing.T) {
	var testData = map[string]struct {
		stringInput string
		expected    *Matrix
	}{
		"empty input": {
			stringInput: "",
			expected:    nil,
		},
		"input with space": {
			stringInput: " ",
			expected:    nil,
		},
		"2 rows * 2 columns": {
			stringInput: "1 2\n3 4",
			expected: &Matrix{
				rows: 2,
				cols: 2,
				data: []int{1, 2, 3, 4},
			},
		},
		"3 rows * 3 columns": {
			stringInput: "1 2 3\n4 5 6\n7 8 9",
			expected: &Matrix{
				rows: 3,
				cols: 3,
				data: []int{1, 2, 3, 4, 5, 6, 7, 8, 9},
			},
		},
		"2 rows * 3 columns": {
			stringInput: "1 2 3\n4 5 6",
			expected: &Matrix{
				rows: 2,
				cols: 3,
				data: []int{1, 2, 3, 4, 5, 6},
			},
		},
		"not number input": {
			stringInput: "a b\nc d",
			expected:    nil,
		},
		"jagged array": {
			stringInput: "1 2 3\n4 5",
			expected:    nil,
		},
	}

	for name, testCase := range testData {
		t.Run(name, func(t *testing.T) {
			result, _ := New(testCase.stringInput)

			if !reflect.DeepEqual(result, testCase.expected) {
				t.Errorf("Expected %v, got %v", testCase.expected, result)
			}
		})
	}
}

func TestMatrix_Rows(t *testing.T) {
	var testData = map[string]struct {
		stringInput string
		expected    [][]int
	}{
		"3 rows * 3 columns": {
			stringInput: "1 2 3\n4 5 6\n7 8 9",
			expected: [][]int{
				{1, 2, 3},
				{4, 5, 6},
				{7, 8, 9},
			},
		},
		"2 rows * 3 columns": {
			stringInput: "1 2 3\n4 5 6",
			expected: [][]int{
				{1, 2, 3},
				{4, 5, 6},
			},
		},
		"3 rows * 2 columns": {
			stringInput: "1 2\n3 4\n5 6",
			expected: [][]int{
				{1, 2},
				{3, 4},
				{5, 6},
			},
		},
	}

	for name, testCase := range testData {
		t.Run(name, func(t *testing.T) {
			matrix, _ := New(testCase.stringInput)
			var result = matrix.Rows()

			if !reflect.DeepEqual(result, testCase.expected) {
				t.Errorf("Expected %v, got %v", testCase.expected, result)
			}
		})
	}
}

func TestMatrix_Cols(t *testing.T) {
	var testData = map[string]struct {
		stringInput string
		expected    [][]int
	}{
		"3 rows * 3 columns": {
			stringInput: "1 2 3\n4 5 6\n7 8 9",
			expected: [][]int{
				{1, 4, 7},
				{2, 5, 8},
				{3, 6, 9},
			},
		},
		"2 rows * 3 columns": {
			stringInput: "1 2 3\n4 5 6",
			expected: [][]int{
				{1, 4},
				{2, 5},
				{3, 6},
			},
		},
		"3 rows * 2 columns": {
			stringInput: "1 2\n3 4\n5 6",
			expected: [][]int{
				{1, 3, 5},
				{2, 4, 6},
			},
		},
	}

	for name, testCase := range testData {
		t.Run(name, func(t *testing.T) {
			matrix, _ := New(testCase.stringInput)
			var result = matrix.Cols()

			if !reflect.DeepEqual(result, testCase.expected) {
				t.Errorf("Expected %v, got %v", testCase.expected, result)
			}
		})
	}
}

func TestMatrix_Set(t *testing.T) {
	var testData = map[string]struct {
		matrix, matrixExpected *Matrix
		row, col, value        int
		expected               bool
	}{
		"row index is negative": {
			matrix: &Matrix{
				rows: 3,
				cols: 3,
				data: []int{1, 2, 3, 4, 5, 6, 7, 8, 9},
			},
			row:      -1,
			col:      2,
			value:    25,
			expected: false,
		},
		"column index is negative": {
			matrix: &Matrix{
				rows: 3,
				cols: 3,
				data: []int{1, 2, 3, 4, 5, 6, 7, 8, 9},
			},
			row:      1,
			col:      -1,
			value:    25,
			expected: false,
		},
		"row index is out of range": {
			matrix: &Matrix{
				rows: 3,
				cols: 3,
				data: []int{1, 2, 3, 4, 5, 6, 7, 8, 9},
			},
			row:      5,
			col:      2,
			value:    25,
			expected: false,
		},
		"column index is out of range": {
			matrix: &Matrix{
				rows: 3,
				cols: 3,
				data: []int{1, 2, 3, 4, 5, 6, 7, 8, 9},
			},
			row:      0,
			col:      15,
			value:    25,
			expected: false,
		},
		"compare matrix after set and expected matrix": {
			matrix: &Matrix{
				rows: 3,
				cols: 3,
				data: []int{1, 2, 3, 4, 5, 6, 7, 8, 9},
			},
			matrixExpected: &Matrix{
				rows: 3,
				cols: 3,
				data: []int{1, 2, 3, 4, 5, 6, 7, 25, 9},
			},
			row:      2,
			col:      1,
			value:    25,
			expected: true,
		},
	}

	for name, testCase := range testData {
		t.Run(name, func(t *testing.T) {

			var result = testCase.matrix.Set(testCase.row, testCase.col, testCase.value)

			if result != testCase.expected {
				t.Errorf("Expected %v, got %v", testCase.expected, result)
			} else if result == true && !reflect.DeepEqual(testCase.matrix, testCase.matrixExpected) {
				t.Errorf("Expected %v, got %v", testCase.matrixExpected, testCase.matrix)
			}
		})
	}
}