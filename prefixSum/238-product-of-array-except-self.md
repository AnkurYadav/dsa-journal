# LC 238 - product-of-array-except-self

**Difficulty:** Medium
**Pattern:** array, prefixProduct
**Link:** https://leetcode.com/problems/product-of-array-except-self

## Approach

Since we need only products of the elements except itself, we can precalculate prefix and suffix sum and then multiply these to get the product required

## Code

```python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
        l = len(nums)
        answer = [1]

        for i in range(l-1):
            answer.append(answer[i] * nums[i])

        next = 1
        for i in range(l-1, -1, -1):
            answer[i] = answer[i] * next
            next = next * nums[i]

        return answer
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

we can't use divide by the number since the number can be zero so we're using product only
