# LC 283 - move-zeroes

**Difficulty:** Easy
**Pattern:** two pointers
**Link:** https://leetcode.com/problems/move-zeroes

## Approach

maintain first pointer at first zero and second pointer at first non-zero, then swap

## Code

```python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        l = len(nums)
        if l < 2:
            return

        i = 0
        j = 1
        while j < l:
            if nums[i] != 0:
                i += 1
                if j < i:
                    j = i+1
                continue
            
            if nums[j] == 0:
                j += 1
                continue
            
            nums[i] = nums[j]
            nums[j] = 0
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

--
