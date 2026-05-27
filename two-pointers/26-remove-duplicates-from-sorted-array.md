# LC 26 - remove-duplicates-from-sorted-array

**Difficulty:** Easy
**Pattern:** two pointers
**Link:** https://leetcode.com/problems/remove-duplicates-from-sorted-array

## Approach

use two pointer one pointer at the end of unique elements and one at checking for duplicates of the first pointer element, whenever a non-duplicate element found swap the next element to the non-duplicate element

## Code

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        l = len(nums)
        if l < 2:
            return l

        i = 0
        j = 1
        while j < l:
            if nums[i] != nums[j]:
                temp = nums[i+1]
                nums[i+1] = nums[j]
                nums[j] = temp
                i+=1
            if nums[l-1] == nums[j]:
                break
            j+=1
        
        return i+1
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

no need to go till end just check if the last element is same as left pointer element
