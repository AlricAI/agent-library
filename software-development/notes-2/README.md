# NOTES

> Mutation testing
https://dev.to/antoinecoulon/dont-target-100-coverage-387o

Regression Testing

Path Coverage: Path coverage is a more advanced type 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
Mutation testing
https://dev.to/antoinecoulon/dont-target-100-coverage-387o

Regression Testing

Path Coverage: Path coverage is a more advanced type of test coverage that ensures every possible path through a given part of the code has been executed. This includes all possible combinations of branches.
  - Example: For a nested if-else statement, path coverage would ensure every possible sequence of decisions is tested.

Statement Coverage: This technique measures the percentage of executable statements in code that are executed at least once during testing. While a high statement coverage indicates thorough testing, it doesn't guarantee all functionalities or logic paths are exercised.
Statement Coverage Statement coverage refers to the percentage of individual statements in the code that have been executed during testing. If a test suite covers 80% statement coverage, it means 80% of the code’s lines or statements have been executed at least once.
  - Example: In the code if (x > 10) { print(x); }, both the condition and the print statement need to be executed to achieve 100% statement coverage.

Branch Coverage: This approach delves deeper than statement coverage. Branch coverage analyzes the percentage of conditional branch statements (if/else statements) where both the true and false paths are executed by test cases. This ensures that coverage tests explore different decision-making scenarios within the code.
Branch Coverage Branch coverage measures the extent to which different branches (true/false outcomes) of decision points (such as if statements) are tested. It ensures that both possible outcomes of each branch are covered.
  - Example: For the statement if (x > 10) { print(x); } else { print(“Small”); }, branch coverage requires that both the if and else branches are executed at least once.

Function Coverage: Function coverage focuses on the percentage of functions within the codebase that are invoked during testing. This technique helps identify functi

*[truncated — see source for full prompt]*