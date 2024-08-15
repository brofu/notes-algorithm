# Parentheses Problems

## Key Points

There are mainly 2 type problems relevant to parentheses

1. Check if the parentheses in string are valid. Usually can be resolved with `stack`
2. Generate valid parentheses in string. Usually can be resolve with `backtrack`

## Thinking Patterns

1. How to check if a string is valid parentheses? 
		a. The number of '(' and ')' should be same, and,
		b. They must be in pair. To be more specific, there should be NO leading ')', and NO open '('

2. How to utilized stack.
		a. Empty stack + ')', means leading ')'
		b. Non-Empty stack + the end, means open '('


## An Example

## Problems

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| 20. Valid Parentheses | [KP in code](../../stack/stack_lc20.go) |  | type 1 | |
| [1249. Minimum Remove to Make Valid Parentheses](https://leetcode.com/problems/minimum-remove-to-make-valid-parentheses/description/) | Stack | | [code](https://github.com/brofu/leetcode/blob/main/stack/stack_lc1249.go) |   |
| 32. Longest Valid Parentheses | | * [stack](../../stack/stack_lc32.go) <br> * [Dynamic Programming](../../dp/dp_lc32.go) | type 1 | |
| 921. Minimum Add to Make Parentheses Valid | [KP in code](./parentheses_lc921.go) | | type 1 | |
| 1541. Minimum Insertions to Balance a Parentheses String | | | * type 1 <br> * TODO: Questions in the code. | |
| 22. Generate Parentheses | [KP in code](../../backtrack/backtrack_lc22.go) | backtrack | type 2 |-|


# References

1. https://labuladong.online/algo/frequency-interview/bracket-problems-summary/
2. https://labuladong.online/algo/essential-technique/backtrack-framework/
3. https://labuladong.online/algo/practice-in-action/generate-parentheses/
