# LC 167 - two-sum-ii-input-array-is-sorted

**Difficulty:** Medium
**Pattern:** two pointers
**Link:** https://leetcode.com/problems/two-sum-ii-input-array-is-sorted

## Approach

since this is a sorted array we can use two pointers here to find the numbers, if the sum of two-pointers is large decrease the sum by moving large pointer down, if the sum is small increase the sum by moving small pointer up, till you reach the solution or pointers cross

## Code

```python
import bisect
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        i = 0
        j = len(numbers) - 1

        while i<j:
            sum = numbers[i] + numbers[j]
            if sum > target:
                j -= 1
            elif sum < target:
                i += 1
            else:
                return [i+1, j+1]
```

```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int i = 0;
        int j = numbers.length - 1;

        while(i < j) {
            int sum = numbers[i] + numbers[j];
            if(sum < target) {
                i++;
            }
            else if(sum > target) {
                j--;
            }
            else {
                break;
            }
        }

        return new int[]{i+1, j+1};
    }
}
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

Use two pointers approach since the array is sorted
