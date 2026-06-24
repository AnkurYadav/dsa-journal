# LC 704 - binary-search

**Difficulty:** Easy
**Pattern:** binary search
**Link:** https://leetcode.com/problems/binary-search

## Approach

since the array is already sorted we can use binary search here

## Code

recursion ->
```java
class Solution {
    public int search(int[] nums, int target) {
        return binarySearch(nums, 0, nums.length - 1, target);
    }

    private int binarySearch(int[] nums, int start, int end, int target) {
        if(start > end) {
            return -1;
        }
        int mid = start + ((end-start)/2);

        if(nums[mid] == target) {
            return mid;
        }
        else if(nums[mid] < target) {
            return binarySearch(nums, mid+1, end, target);
        }
        else {
            return binarySearch(nums, start, mid - 1, target);
        }
    }
}
```

loop ->
```java
class Solution {
    public int search(int[] nums, int target) {
        int i = 0;
        int j = nums.length - 1;

        while(i <= j) {
            int mid = i + ((j-i)/2);

            if(nums[mid] == target) {
                return mid;
            }
            else if(nums[mid] > target) {
                j = mid - 1;
            }
            else {
                i = mid + 1;
            }
        }

        return -1;
    }
}
```

## Complexity

- Time: O(log(N))
- Space: O(log(N)) -> recursion , O(1) -> loop

## Gotcha

loop is more space efficient than recursion because of recursion stack
