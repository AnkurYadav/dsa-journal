search-in-rotated-sorted-array
# LC 33 - search-in-rotated-sorted-array

**Difficulty:** Medium
**Pattern:** binary search
**Link:** https://leetcode.com/problems/search-in-rotated-sorted-array

## Approach

use indices as normal sorted array for binary search but when fetching actual element use actual rotated index.

## Code

```java
class Solution {
    public int search(int[] nums, int target) {
        int k = 0;
        for(int i = 1; i < nums.length; i++) {
            if(nums[i] < nums[i-1]) {
                k = i;
            }
        }

        int lo = 0;
        int hi = nums.length - 1;
        while(lo <= hi) {
            int mid = lo + ((hi - lo)/2);

            int midRotatedI = (mid + k) % nums.length;

            if(nums[midRotatedI] == target) {
                return midRotatedI;
            }
            else if(nums[midRotatedI] < target) {
                lo = mid + 1;
            }
            else {
                hi = mid - 1;
            }
        }

        return -1;
    }
}
```

## Complexity

- Time: O(N + log(N))
- Space: O(1)

## Gotcha

rotated index can be calculated using remainder operator
