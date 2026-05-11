# LC 01 - two-sum

**Difficulty:** Easy
**Pattern:** hashmap
**Link:** https://leetcode.com/problems/two-sum/description/

## Approach



## Code

### sol 1:

```python
import bisect

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        # sort the array
        sorted_nums = sorted(nums)

        # iterate the array
        for i in range(len(nums)) :
            n1 = nums[i]
            # number to find in array
            n2 = target - n1

            # find in sorted array quickly using binary search
            sorted_i = self.find_sorted_index(sorted_nums, n2)
            if sorted_i != -1:
                # if found get the actual index
                i2 = self.find_index(nums, n2, i)
                if i2 != -1:
                    return [i, i2]
                

    def find_index(self, arr: List[int], num: int, skip_index: int) -> int:
        for i in range(len(arr)):
            if skip_index == i:
                continue
            else:
                if arr[i] == num:
                    return i
        return -1

    def find_sorted_index(self, arr: List[int], num: int) -> int:
        i = bisect.bisect_left(arr,num)
        if i != len(arr) and arr[i] == num:
            return i
        return -1
```

### sol2:
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        index_dict = {}

        for i in range(len(nums)):
            n2 = target - nums[i]
            if n2 in index_dict:
                return [i, index_dict[n2]]
            index_dict[nums[i]] = i
```

## Complexity

sol 1
- Time: O(nlog(n))
- Space: O(n)

sol 2
- Time: O(n)
- Space: O(n)

## Gotcha

Use hashmap to find the element in O(1), you used binary_search to find the element after sorting the array which was not required since index were changed after update
