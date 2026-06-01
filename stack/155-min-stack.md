# LC 155 - min-stack

**Difficulty:** Medium
**Pattern:** stack
**Link:** https://leetcode.com/problems/min-stack

## Approach

we need to store the min value at every stage

## Code

```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.length = 0

    def push(self, val: int) -> None:
        if self.length > 0:
            min_till_now = self.getMin()
        else:
            min_till_now = val
        self.stack.append((val, min(val, min_till_now)))
        self.length += 1

    def pop(self) -> None:
        self.stack.pop()
        self.length -= 1

    def top(self) -> int:
        return self.stack[self.length - 1][0]

    def getMin(self) -> int:
        return self.stack[self.length - 1][1]


# Your MinStack object will be instantiated and called as such:
# obj = MinStack()
# obj.push(val)
# obj.pop()
# param_3 = obj.top()
# param_4 = obj.getMin()
```

## Complexity

- Time: O(1)
- Space: O(n)

## Gotcha

we need to store the min value at every stage since after a pop operation we don't want to calculate new min
