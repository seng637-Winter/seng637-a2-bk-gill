**SENG 637 - Software Testing, Reliability, and Quality**

**Lab. Report \#2 – Requirements-Based Test Generation**

| Group #:  18  |  ID |
| -------------- | --- |
| Student Names: | ########    |
| Balkarn Gill   |             |
| Taran Bains    | ########    |
| Satchytan K.   |             |
| Chioma         |             |
| Hannah         |             |

# 1 Introduction

Our goal was to learn and apply unit testing techniques to the JFreeChart library, focusing on developing a comprehensive understanding of automated testing, particularly with JUnit. We aimed to design tests based on the requirements of specific units and to integrate mock objects effectively.

# 2 Detailed description of unit test strategy

Our unit test strategy was centered around black-box testing principles, emphasizing equivalence partitioning and boundary value analysis to ensure thorough coverage of the system's functionality without relying on its internal workings.

**Input Partitions Designed:**

**Range Class:**

Negative Ranges: Inputs where both lower and upper bounds are negative.
Positive Ranges: Inputs where both bounds are positive.
Zero-Spanning Ranges: Inputs where the range spans zero, including one positive and one negative bound.
Single-Point Ranges: Inputs where the lower and upper bounds are the same.

**DataUtilities Class:**

Empty Datasets: Tests with no data to ensure graceful handling.
Positive Data Sets: Datasets with all positive values.
Mixed Data Sets: Datasets with a mix of positive, negative, and zero values.

# 3 Test cases developed

For each partition designed, we developed corresponding test cases. Here are the test methods and classes organized by the source code method they test:

**org.jfree.data.Range Tests:**

testRangeWithNegativeValues(): Tests negative ranges. Covers the Negative Ranges partition.
testRangeWithPositiveValues(): Tests positive ranges. Covers the Positive Ranges partition.
testRangeSpanningZero(): Tests ranges that span zero. Covers the Zero-Spanning Ranges partition.
testSinglePointRange(): Tests ranges where the lower and upper bounds are equal. Covers the Single-Point Ranges partition.

**org.jfree.data.DataUtilities Tests:**

testEmptyDataset(): Tests handling of empty datasets. Covers the Empty Datasets partition.
testPositiveDatasetTotal(): Tests calculation of totals from datasets with all positive values. Covers the Positive Data Sets partition.
testMixedDatasetTotal(): Tests calculation from datasets with mixed values. Covers the Mixed Data Sets partition.

// write down the name of the test methods and classes. Organize the based on
the source code method // they test. identify which tests cover which partitions
you have explained in the test strategy section //above

# 4 How the team work/effort was divided and managed

Our team consisted of five members, and we aimed for an equitable distribution of tasks and responsibilities to leverage our diverse skill sets and ensure that each member contributed meaningfully to the project.

# 5 Difficulties encountered, challenges overcome, and lessons learned

**Difficulties Encountered:**

Initial challenges with setting up JUnit and understanding mocking frameworks.
Difficulty in designing test cases that adequately cover all partitions without internal knowledge of the code.

**Challenges Overcome:**

Through collaboration and research, we were able to overcome setup issues and gain a better understanding of JUnit and mocking.
We applied black-box testing techniques rigorously to ensure comprehensive test coverage.

**Lessons Learned:**

The importance of clear communication and division of responsibilities within the team.
The value of thorough testing in identifying and mitigating potential issues in software development.

# 6 Comments/feedback on the lab itself

We found the lab to be an invaluable practical exercise in understanding unit testing's principles and applications. The focus on JFreeChart provided a complex yet accessible challenge that helped solidify our theoretical knowledge through hands-on practice. While the lab was well-structured and informative, we suggest providing more examples and guidance on using mocking frameworks, as this was a significant learning curve for us. Overall, the lab was a highly beneficial component of our learning experience, offering insights that we will carry into our future software development endeavors.
