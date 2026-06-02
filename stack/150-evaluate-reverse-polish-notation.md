# LC 150 - evaluate-reverse-polish-notation

**Difficulty:** Medium
**Pattern:** stack
**Link:** https://leetcode.com/problems/evaluate-reverse-polish-notation

## Approach

use stack to keep track of last two numbers to operate on whenever a operand is found get last two numbers from stack and operate on them then push back the result onto stack

## Code

```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        num_stack = []

        operands = {'+', '-', '*', '/'}

        for token in tokens:
            if token in operands:
                num2 = num_stack.pop()
                num1 = num_stack.pop()
                res = self.doOperation(num1, num2, token)
                num_stack.append(res)
            else:
                num_stack.append(int(token))

        return num_stack.pop()

    def doOperation(self, num1: int, num2: int, operand: str) -> int:
        match operand:
            case '+':
                return num1 + num2
            case '-':
                return num1 - num2
            case '*':
                return num1 * num2
            case '/':
                return int(num1 / num2)
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

keep in mind the order of numbers to be operated on operand
