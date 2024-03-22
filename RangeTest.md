## Range Class
The test range of -50.0 to 60.0 will be used for most test cases. This range was chosen because it has positive, negative and zero numbers, making it very robust. Depending on the test case, additional test ranges were created for more specific test case scenarios.

#### **Table 1.** Boundary Value Testing - Domain Table for Range Class
| Boundary Value (BVT) Notation      | Value      |
|:----------------------------------:|:----------:|
| BLB (value just below lower bound) | -50.00001 |
| LB (lower bound)                   | -50.0       |
| ALB (value just above lower bound) | -49.99999  |
| Nominal Value(s)                   | -49 to 59  |
| BUB (value just below upper bound) | 59.99999   |
| UB (upper bound)                   |    60.0     |
| AUB (value just above upper bound) | 60.00001  |


#### **Table 3.** Range.expandToInclude() Test Cases
| Test Case Name                   | Input Value Partitions                                | Expected Value                  | Actual Value            | Outcome |
|----------------------------------|-------------------------------------------------------|:-------------------------------:|:-----------------------:|:-------:|
| expandToIncludeBelowLowerBound() | Input range:(-50.00001,60.0); Input value: -50.00001  | (-50.00001, 60.0)               | (-50.0,-50.0)           | Fail    |
| expandToIncludeLowerBound()      | Input range:(-50.0,60.0); Input value: -50.0          | (-50.0,60.0)                    | IllegalArgumentException | Fail    |
| expandToIncludeAboveLowerBound() | Input range:(-50.0,60.0); Input value: -49.99999      | (-50.0,60.0)                    | (-50.0,60.0)            | Pass    |
| expandToIncludeNominalValue()    | Input Range:(-50.0,60.0); Input value: 20.0           | (-50.0,60.0)                    | (-50.0,60.0)            | Pass    |
| expandToIncludeBelowUpperBound() | Input Range:(-50.0,60.0); Input value: 59.99999       | (-50.0,60.0)                    | (-50.0,60.0)            | Pass    |
| expandToIncludeUpperBound()      | Input Range:(-50.0,60.0); Input value: 60.0           | (-50.0,60.0)                    | (-50.0,60.0)            | Pass    |
| expandToIncludeAboveUpperBound() | Input Range:(-50.0,60.0); Input value: 60.00001       | (-50.0,60.00001)                | (-50.0,60.00001)        | Pass    |
| expandToIncludeMaxValue()        | Input Range:(-50.0,60.0); Input value: Double.MAX_VALUE | (-50.0,Double.MAX_VALUE)      | (-50.0,Double.MAX_VALUE) | Pass    |
| expandToIncludeMinValue()        | Input Range:(-50.0,60.0); Input value: Double.MIN_VALUE | (-50.0,Double.MIN_VALUE)      | (-50.0,Double.MIN_VALUE) | Pass    |
| expandToIncludeNullRange()       | Input Range: (15.0,15.0); Input value: null           | (15.0,15.0)                     | (15.0,15.0)             | Pass    |


#### **Table 4.** Range.contains() Test Cases
| Test Case Name                                    | Input Value Partitions                                | Expected Value                  | Actual Value            | Outcome |
|---------------------------------------------------|-------------------------------------------------------|:-------------------------------:|:-----------------------:|:-------:|
| containsValueJustBelowLowerBound()                | exampleRange: (-50.0,60.0); Value: -50.00001          | False                           | False                   | Pass    |
| containsLowerBound()                              | exampleRange: (-50.0,60.0); Value: -50.0              | True                            | True                    | Pass    |
| containsValueJustAboveLowerBound()                | exampleRange: (-50.0,60.0); Value: -49.99999          | True                            | True                    | Pass    |
| containsNominalValue()                            | exampleRange: (-50.0,60.0); Value: 0                  | True                            | True                    | Pass    |
| containsValueJustBelowUpperBound()                | exampleRange: (-50.0,60.0); Value: 59.99999           | True                            | True                    | Pass    |
| containsUpperBound()                              | exampleRange: (-50.0,60.0); Value: 60.0               | True                            | True                    | Pass    |
| containsValueJustAboveUpperBound()                | exampleRange: (-50.0,60.0); Value: 60.00001           | False                           | False                   | Pass    |
| containsNotANumber()                              | exampleRange: (-50.0,60.0); Value: Double.NaN         | False                           | False                   | Pass    |
| containsACharacter()                              | exampleRange: (-50.0,60.0); Value: ‘%’                | False                           | True                    | Fail    |
| containsValueInRangeWithNegativeBoundaries()      | exampleRange: (-20.0, -10.0); Value: -13.0            | True                            | True                    | Pass    |
| containsValueEqualToBothLowerAndUpperBoundaries() | exampleRange: (11.0, 11.0); Value: 11.0               | True                            | True                    | Pass    |


#### **Table 5.** Range.combine() Test Cases
| Test Case Name                   | Input Value Partitions                                | Expected Value                  | Actual Value            | Outcome |
|----------------------------------|-------------------------------------------------------|:-------------------------------:|:-----------------------:|:-------:|
| testCombineBothNull()            | Range 1: null; Range 2: null                          | null                            | null                    | Pass    |
| testCombineRange1Null()          | Range 1: (-50.0,60.0); Range 2: null                  | (-50.0,60.0)                    | (-50.0,60.0)            | Pass    |
| testCombineBothNotNull           | Range 1: (1.0, 5.0); Range 2: (3.0, 8.0)              | (1.0, 8.0)                      | IllegalArgumentException | Fail   |
| testCombineEmptyRanges()         | Range 1: (5.0, 5.0); Range 2: (5.0, 5.0)              | (5.0, 5.0)                      | (5.0, 5.0)              | Pass    |
| testCombineOneInsideOther()      | Range 1: (1.0, 10.0); Range 2: (3.0, 8.0)             | (1.0, 10.0)                     | IllegalArgumentException | Fail  |
| testCombineTouchingRanges()      | Range 1: (1.0, 5.0); Range 2: (5.0, 10.0)             | (1.0, 10.0)                     | IllegalArgumentException | Fail    |


#### **Table 6.** Range.intersects() Test Cases
| Test Case Name                   | Input Value Partitions                                | Expected Value                  | Actual Value            | Outcome |
|----------------------------------|-------------------------------------------------------|:-------------------------------:|:-----------------------:|:-------:|
| intersectsWithBLBAndLB() | exampleRange: (-50.0,60.0); value:  -50.00001, -50.0 | True | True | Pass|
| intersectsWithBLBAndALB() | exampleRange: (-50.0,60.0); value:  -50.00001, -49.99999 | True | True | Pass |
| intersectsWithBLBAndAUB() | exampleRange: (-50.0,60.0); value:  -50.00001, 60.00001 | True | True | Pass |
| intersectsWithLBAndALB() | exampleRange: (-50.0,60.0); value:  -50.0, -49.99999 | True | True | Pass |
| intersectsWithLBAndUB() | exampleRange: (-50.0,60.0); value:  -50.0, 60.0 | True | True | Pass |
| intersectsWithNormalAndNormal() | exampleRange: (-50.0,60.0); value:  -49.0, 59.0 | True | True | Pass |
| intersectsWithBUBAndUB() | exampleRange: (-50.0,60.0); value:  59.99999, 60.0 | True | False | Fail |
| intersectsWithBUBAndAUB() | exampleRange: (-50.0,60.0); value:  59.99999, 60.00001 | True | False | Fail |
| intersectsWithUBAndAUB() | exampleRange: (-50.0,60.0); value:  60.0, 60.00001 | True | False | Fail |
| intersectsWithInputAUBAndMAX() | exampleRange: (-50.0,60.0); value:  60.00001, Double.MAX_VALUE | False | False | Pass |
| intersectsWithInputBLBAndMIN() | exampleRange: (-50.0,60.0); value:  -999.00, -50.00001 | False | True | Fail |
| intersectsWithInputNaNAnd1() | exampleRange: (-50.0,60.0); value:  Double.NaN, 1 | False | False | Pass |


#### **Table 7.** Range.shift() Test Cases
| Test Case Name                   | Input Value Partitions                                | Expected Value                  | Actual Value            | Outcome |
|----------------------------------|-------------------------------------------------------|:-------------------------------:|:-----------------------:|:-------:|
| positiveShiftRangeRight() | exampleRange: (-50.0,60.0); delta: 50.0 | (0.0,110.0) | (0.0,110.0) | Pass |
| negativeShiftRangeLeft() | exampleRange: (-50.0,60.0); delta: -25.0 | (-75.0, 35.0) | (-75.0, 35.0) | Pass |
| zeroDeltaNoShiftRange() | exampleRange: (-50.0,60.0); delta: 0.0 | (-50.0,60.0) | (-50.0,60.0) | Pass |
| positiveShiftLbZeroCrossing()| exampleRange: (-50.0,60.0); delta: 50.00001 | (0.0, 110.00001) | [1.0000000003174137E-5, 1.0000000003174137E-5] | Fail |
| positiveShiftLbAndUbZeroCrossing() | exampleRange: (-50.0,60.0); delta: 50.00001 | (0.0, 0.0) | [1.0000000003174137E-5, 1.0000000003174137E-5] | Fail |
| negativeShiftUbZeroCrossing() | exampleRange: (-50.0,60.0); delta: -50.00001 | (0.0, 99.99999) | [-1.0000000003174137E-5, -1.0000000003174137E-5] | Fail |
| negativeShiftLbAndUbZeroCrossing() | exampleRange: (-50.0,60.0); delta: -100.00001 | (0.0, 0.0) | [-50.00001,-50.00001]  | Fail |
| nullBaseInvalidParameterException() | exampleRange: (-50.0,60.0); delta: 10.0 | InvalidParameterException | NullPointerException | Fail |
