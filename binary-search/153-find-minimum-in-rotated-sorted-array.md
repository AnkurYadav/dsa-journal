# LC 153 - find-minimum-in-rotated-sorted-array

**Difficulty:** Medium
**Pattern:** binary search
**Link:** https://leetcode.com/problems/find-minimum-in-rotated-sorted-array

## Approach

we can find the minimum by discarding the half of the array in which we know for sure minimum is not present

## Code

```java
class Solution {
    public int findMin(int[] nums) {
        int lo = 0;
        int hi = nums.length - 1;

        while(lo < hi) {
            int mid = lo + ((hi - lo) / 2);

            if(nums[mid] > nums[hi]) {
                lo = mid+1;
            }
            else{
                hi = mid;
            }
        }

        return nums[lo];
    }
}
```

## Complexity

- Time: O(log(N))
- Space: O(1)

## Gotcha

take care of the limits and conditions
