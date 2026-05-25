# LC 209 - minimum-size-subarray-sum

**Difficulty:** Easy
**Pattern:** sliding window
**Link:** https://leetcode.com/problems/minimum-size-subarray-sum

## Approach

use sliding window, it grows from right until we get a greater or equal sum then we shrink it from left until we get a lesser sum and repeat this process till end

## Code

```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        l = len(nums)
        if l == 0:
            return 0
        i = 0
        j = 0
        min_len = l+1
        curr_sum = nums[0]
        while i <= j and j < l:
            if curr_sum >= target:
                min_len = min(min_len, j-i+1)
                curr_sum -= nums[i]
                i += 1
            else:
                j += 1
                if j == l:
                    break
                curr_sum += nums[j]

        if min_len == l+1:
            min_len = 0

        return min_len
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

last element should be checked carefully
