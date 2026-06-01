# LC 20 - valid-parentheses

**Difficulty:** Easy
**Pattern:** stack
**Link:** https://leetcode.com/problems/valid-parentheses

## Approach

use stack to match the last paranthesis

## Code

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []
        for ch in s:
            if ch == '(' or ch == '{' or ch == '[':
                stack.append(ch)
            else:
                if not stack:
                    return False
                prev_ch = stack.pop()
                if ch == ')' and prev_ch != '(':
                    return False
                elif ch == '}' and prev_ch != '{':
                    return False
                elif ch ==']' and prev_ch != '[':
                    return False
        return len(stack) == 0
```

## Complexity

- Time: O(n)
- Space: O(n)

## Gotcha

check for stack emptiness in loop also
