# LC 739 - daily-temperatures
 | Hard
**Pattern:** monotonic stack
**Link:** https://leetcode.com/problems/daily-temperatures

## Approach

use monotonic stack to keep track of indices for which we have not found greater temperature than them, and compare with current temperatures and push current on stack

## Code

```java
class Solution {
    public int[] dailyTemperatures(int[] temperatures) {
        int[] result = new int[temperatures.length];
        Deque<Integer> monotonicStack = new ArrayDeque<>();

        for(int i = 0; i < temperatures.length; i++) {
            if(monotonicStack.isEmpty()) {
                monotonicStack.push(i);
            }
            else {
                while(!monotonicStack.isEmpty() && temperatures[i] > temperatures[monotonicStack.peek()]) {
                    int prev_i = monotonicStack.pop();
                    result[prev_i] = i - prev_i;
                }
                monotonicStack.push(i);
            }
        }

        return result;
    }
}
```

## Complexity

- Time: O(N)
- Space: O(N)

## Gotcha

Use monotonic stack to keep track of indices which would help in calculating distance
