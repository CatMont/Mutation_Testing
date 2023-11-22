# Mutation_Testing

## Introduction

Mutation testing is a powerful technique to evaluate the effectiveness of a test suite by introducing small changes (mutations) to the source code and observing how well the tests detect these changes. In this report, I utilize the MutPy mutation testing framework to assess the robustness of the test suite for the Polynomial class.

## Mutation Operators

The operators outlined in this section are run by mutpy using the command below: 

```
mut.py --target Polynomial.py --unit-test PolyTest.py -m --runner pytest
```

Arithmetic Operator Replacement:
- Replaces arithmetic operators such as +, -, *, /, etc., with their counterparts to assess the resilience of the test suite to changes in arithmetic operations.

Comparison Operator Replacement:
- Modifies comparison operators such as <, <=, >, >=, ==, != to evaluate how well the test suite can identify changes in conditional statements.

Logical Connector Replacement:
- Alters logical connectors such as and, or, and not to check the effectiveness of the test suite in handling changes in logical conditions.

Assignment Operator Replacement:
- Changes assignment operators like =, +=, -=, etc., to assess the impact on variable assignments.

Unary Operator Replacement:
- Modifies unary operators such as +, -, ~ to check if the test suite can identify changes in unary expressions.

Statement Deletion:
- Deletes statements to evaluate how well the test suite can detect missing or deleted code.

Return Value Replacement:
- Alters return values to assess the ability of the test suite to identify changes in function return values.

Break/Continue Replacement:
- Replaces break and continue statements to evaluate the impact on loop control flow.

Decorator Removal:
- Removes decorators to check if the test suite can detect changes in the application of decorators.

Exception Handling Modification:
- Modifies exception handling statements to assess how well the test suite can identify changes in error-handling logic.



## Summarize Surviving and Killing 

After applying the mutation operators to the Polynomial class, the MutPy framework was used to run the test suite against the mutants. The results are summarized as follows:
- Survived Mutants: Mutants that the test suite did not detect. These indicate potential weaknesses in the test suite.
- Killed Mutants: Mutants that the test suite successfully identified. These demonstrate the effectiveness of the test suite in detecting changes.
- Incompetent: Indicates that the test suite does not allow for mutant operators to work effectively. Generally, this means that the existing tests do not provide enough coverage for mutant operators to be functional. 

 __The initial results:__

```
[*] Mutation score [10.27966 s]: 54.3%
   - all: 89
   - killed: 25 (28.1%)
   - survived: 21 (23.6%)
   - incompetent: 43 (48.3%)
   - timeout: 0 (0.0%)
```
## Analysis of Test Suite Effectiveness 

Overall, the test suite received a mutation score of 54.3%, but in order to demonstrate a robust and effective testing suite, 
this number should be as close to 100% as possible. 

It is ideal to have more killed mutants than survived ones, as this demonstrates that the testing suite is catching the mutations and proving its effectiveness. However, incompetent demonstrates that there are either not enough tests or that the tests that exist are too poorly written to properly employ the mutation operators
against the test suite. 

```
[*] Mutation score [11.53777 s]: 56.5%
   - all: 89
   - killed: 26 (29.2%)
   - survived: 20 (22.5%)
   - incompetent: 43 (48.3%)
   - timeout: 0 (0.0%)
```



## Recommendations for Improving the Test Suite

- Enhance Coefficient Checking: Strengthen tests related to polynomial coefficients to better detect changes in coefficient values.

- Diversify Test Cases: Introduce test cases that cover a broader range of scenarios, including edge cases and different polynomial degrees.
    
- Improve Arithmetic Operation Tests: Ensure thorough testing of arithmetic operations, considering various combinations of positive and negative coefficients.


Below are tests that were added to demonstrate minor modifications of the test suite. These are tests for evaluate() and get_derivative_coefficients() 
from the Polynomial class, which did not have unit tests prior to the additions shown below. 

 ```
def test_evaluate(): 
    poly = Polynomial([3, 0, 2]) 
    result = poly.evaluate(2)
    assert result == 14

def test_derivative_coefficient():
    poly2 = Polynomial([1, -1])  
    result = poly2.get_derivative_coefficients()
    assert result == [0]
 ```

 By adding these tests, more mutations can be killed. 
 By running the mutpy command referenced earlier in this report again, these results are obtained: 

 
 ```
[*] Mutation score [11.75337 s]: 60.0%
   - all: 89
   - killed: 27 (30.3%)
   - survived: 18 (20.2%)
   - incompetent: 44 (49.4%)
   - timeout: 0 (0.0%)
```


## Conclusion: 

Mutation testing using MutPy provides valuable insights into the effectiveness of the test suite for the Polynomial class.
By identifying areas of strength and weakness, this analysis guides improvements to enhance the overall reliability of the test suite, 
contributing to the robustness of the Polynomial class implementation. Continuous refinement of the test suite based on mutation testing 
results is essential for maintaining a high level of code quality and reliability.

