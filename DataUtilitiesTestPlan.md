# Test Plan

## DataUtilities

### Method 1: calculateColumnTotal

public static double calculateColumnTotal(Values2D data, int column)
Returns the sum of the values in one column of the supplied data table. With invalid input, a total of zero will be returned.

### Partitions

#### data

     the table of values (null not permitted)

- expected:
  - array with width more than one and height more than one
  - array with width equals to one and height more than one
  - array with width more than one and height equals to one
  - array with width equals to one and height equals to one
- unexpected
  - null

#### column

     the column index

- expected:
  - int in range of [0, (the number of columns - 1)]
- unexpected
  - less than zero
  - more than the number of columns

| Test Case                                | Description                                    | Data                         | Column | Expected |
| ---------------------------------------- | ---------------------------------------------- | ---------------------------- | ------ | -------- |
| testCalculateColumnTotalWithColumnZero   | to test the function with first column         | [[0, 1, 2], [10, 20, 30]]    | 0      | 10       |
| testCalculateColumnTotalWithMissingValue | to test the function with missing values       | [[0, null, 2], [10, 20, 30]] | 1      | 20       |
| testCalculateColumnTotalBasic            | to test the function with normal inputs        | [[0, 1, 2], [10, 20, 30]]    | 1      | 21       |
| testCalculateColumnTotalLastColumn       | to the the function with last column           | [[0, 1, 2], [10, 20, 30]]    | 2      | 32       |
| testCalculateColumnTotalOneRow           | to test the function with a data of one row    | [[0, 1, 2]]                  | 1      | 1        |
| testCalculateColumnTotalOneColumn        | to test the function with a data of one column | [[10], [20]]                 | 0      | 30       |

| Test Case                                | Expected | Actual | PASS/FAIL | Technique |
| ---------------------------------------- | -------- | ------ | --------- | --------- |
| testCalculateColumnTotalWithColumnZero   | 10       | 10     | PASS      | BVA LB    |
| testCalculateColumnTotalWithMissingValue | 20       | 21     | FAIL      | ECT       |
| testCalculateColumnTotalBasic            | 21       | 21     | PASS      | ECT       |
| testCalculateColumnTotalLastColumn       | 32       | 32     | PASS      | BVA UB    |
| testCalculateColumnTotalOneRow           | 1        | 1      | PASS      | ECT       |
| testCalculateColumnTotalOneColumn        | 30       | 30     | PASS      | ECT       |

### Method 2: calculateRowTotal

public static double calculateRowTotal(Values2D data, int row)
Returns the sum of the values in one row of the supplied data table. With invalid input, a total of zero will be returned.

### Partitions

#### data

     the table of values (null not permitted)

- expected:
  - array with width more than one and height more than one
  - array with width equals to one and height more than one
  - array with width more than one and height equals to one
  - array with width equals to one and height equals to one
- unexpected
  - null

#### row

     the column index

- expected:
  - int in range of [0, (the number of row - 1)]
- unexpected
  - less than zero
  - more than the number of rows

| Test Case                             | Description                                    | Data                         | Row | Expected |
| ------------------------------------- | ---------------------------------------------- | ---------------------------- | --- | -------- |
| testCalculateRowTotalWithRowZero      | to test the function with first row            | [[0, 1, 2], [10, 20, 30]]    | 0   | 0        |
| testCalculateRowTotalWithMissingValue | to test the function with missing values       | [[0, null, 2], [10, 20, 30]] | 0   | 2        |
| testCalculateRowTotalBasic            | to test the function with normal inputs        | [[0, 1, 2], [10, 20, 30]]    | 0   | 3        |
| testCalculateRowTotalLastRow          | to the the function with last row              | [[0, 1, 2], [10, 20, 30]]    | 1   | 60       |
| testCalculateRowTotalOneRow           | to test the function with a data of one row    | [[0, 1, 2]]                  | 0   | 3        |
| testCalculateRowTotalOneColumn        | to test the function with a data of one column | [[10] [20]]                  | 0   | 10       |

| Test Case                             | Expected | Actual | PASS/FAIL | Technique |
| ------------------------------------- | -------- | ------ | --------- | --------- |
| testCalculateColumnTotalWithRowZero   | 3        | 1      | FAIL      | BVA LB    |
| testCalculateRowTotalWithMissingValue | 2        | 0      | FAIL      | ECT       |
| testCalculateRowTotalBasic            | 3        | 1      | FAIL      | ECT       |
| testCalculateRowTotalLastRow          | 60       | 30     | FAIL      | BVA UB    |
| testCalculateRowTotalOneRow           | 3        | 1      | FAIL      | ECT       |
| testCalculateRowTotalOneColumn        | 10       | 0      | FAIL      | ECT       |

### Method 3: createNumberArray

public static java.lang.Number[] createNumberArray(double[] data)
Constructs an array of Number objects from an array of double primitives.

### Partitions

#### data

     An array of double primitives

- expected:
  - array of size more than one
  - array of size one
  - array of size zero
- unexpected
  - null

| Test Case                                | Description                              | Data      | Expected                |
| ---------------------------------------- | ---------------------------------------- | --------- | ----------------------- |
| testCreateNumberArrayWithSizeMoreThanOne | to test array with size of more than one | [1 2 ...] | number array([1 2 ...]) |
| testCreateNumberArrayWithSizeOne         | to test array with size one              | [5]       | number array([5])       |
| testCreateNumberArrayWithSizeZero        | to test array with size zero             | []        | number array([])        |

| Test Case                                | Expected                | Actual           | PASS/FAIL | Technique |
| ---------------------------------------- | ----------------------- | ---------------- | --------- | --------- |
| testCreateNumberArrayWithSizeMoreThanOne | number array([1 2 ...]) | null             | FAIL      | ECT       |
| testCreateNumberArrayWithSizeOne         | number array([5])       | null             | FAIL      | BVA ALB   |
| testCreateNumberArrayWithSizeZero        | number array([])        | number array([]) | PASS      | BVA LB    |

### Method 4: createNumberArray2D

public static java.lang.Number[][] createNumberArray2D(double[][] data)
Constructs an array of arrays of Number objects from a corresponding structure containing double primitives.

### Partitions

#### data

     An array of 2D double primitives (null not permitted)

- expected:
  - array of size more than one row and column
  - array with one column
  - array with one row
  - array with zero column
  - array with zero row
- unexpected
  - null

| Test Case                             | Description                        | Data        | Expected                        |
| ------------------------------------- | ---------------------------------- | ----------- | ------------------------------- |
| testCreateNumberArray2dNullInput      | to test the null input as an input | null        | IllegalArgumentException        |
| testCreateNumberArray2d               | to test multi-dimensional array    | [[10 x 10]] | number array([[0.0, 1.1, ...]]) |
| testCreateNumberArray2dWithSizeZero   | to test array with size of zero    | [[]]        | number array([[]])              |
| testCreateNumberArray2dWithZeroColumn | to test array with zero column     | [[]]        | number array([[]])              |
| testCreateNumberArray2dWithOneRow     | to test array with one row         | [[1 2 ...]] | number array([[1 2 ...]])       |
| testCreateNumberArray2dWithOneColumn  | to test array with one column      | [[1 2 ...]] | number array([[1 2 ...]])       |

| Test Case                             | Expected                        | Actual                   | PASS/FAIL | Technique |
| ------------------------------------- | ------------------------------- | ------------------------ | --------- | --------- |
| testCreateNumberArray2dNullInput      | IllegalArgumentException        | IllegalArgumentException | PASS      | ECT       |
| testCreateNumberArray2d               | number array([[0.0, 1.1, ...]]) | null                     | FAIL      | ECT       |
| testCreateNumberArray2dWithSizeZero   | number array([[]])              | number array([[]])       | PASS      | BVA LB    |
| testCreateNumberArray2dWithZeroColumn | number array([[]])              | number array([[]])       | PASS      | BVA LB    |
| testCreateNumberArray2dWithOneRow     | number array([[1 2 ...]])       | null                     | FAIL      | BVA ALB   |
| testCreateNumberArray2dWithOneColumn  | number array([[1 2 ...]])       | null                     | FAIL      | BVA ALB   |

### Method 5: getCumulativePercentage

Test Case Plan and Design For getCumulativePercentage

1. Valid Input Test Case
   • Objective: Verify that the method correctly calculates cumulative percentages for a standard set of values.
   • Input: A KeyedValues object with a known set of numeric values.
   • Expected Output: A KeyedValues object with cumulative percentages corresponding to the input values.
2. Empty Input Test Case
   • Objective: Verify the method's behavior with an empty KeyedValues object.
   • Input: An empty KeyedValues object.
   • Expected Output: An empty KeyedValues object (or possibly a specific behavior defined in the requirements, such as throwing an exception).
3. Null Input Test Case
   • Objective: Verify the method's response to a null input.
   • Input: null.
   • Expected Output: An InvalidParameterException is thrown.
4. Negative Values Input Test Case
   • Objective: Assess how the method handles negative values.
   • Input: A KeyedValues object containing negative values.
   • Expected Output: A KeyedValues object with correctly calculated cumulative percentages, assuming negative values are valid for the application context.
5. Large Values Input Test Case
   • Objective: Test the method's ability to handle large numbers without overflow or precision loss.
   • Input: A KeyedValues object with very large values.
   Expected Output: Correct cumulative percentages, demonstrating the method's numerical stability.
   Test Plan Results Results:

| Test | Test Method             | Passed | Expected Values      | Actual Values        |
| ---- | ----------------------- | ------ | -------------------- | -------------------- |
| 1    | testEmptyInput          | Yes    | N/A                  | N/A                  |
| 2    | testLargeValuesInput    | Yes    | [0.16667, 0.5, 1.0]  | [0.16667, 0.5, 1.0]  |
| 3    | testValidInput          | Yes    | [0.3125, 0.875, 1.0] | [0.3125, 0.875, 1.0] |
| 4    | testNegativeValuesInput | Yes    | [1.0]                | [1.0]                |
| 5    | testNullInput           | Yes    | N/A                  | N/A                  |
