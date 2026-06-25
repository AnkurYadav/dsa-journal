# LC 128 - longest-consecutive-sequence

**Difficulty:** Medium
**Pattern:** hashset
**Link:** https://leetcode.com/problems/longest-consecutive-sequence

## Approach

Use set to check in O(1) if next number is there or not

## Code

```python
class Solution:
    def longestConsecutive(self, nums: List[int]) -> int:
        nums_set = set(nums)

        longest_sequence = 0
        current_sequence = 0
        for i in nums_set:
            if i-1 not in nums_set:
                j = i+1
                current_sequence = 1
                while j in nums_set:
                    current_sequence += 1
                    j += 1
                longest_sequence = max(longest_sequence, current_sequence)

        return longest_sequence
```

```java
class Solution {
    public int longestConsecutive(int[] nums) {
        Set<Integer> set = new HashSet<>();
        for(int n : nums) {
            set.add(n);
        }

        int maxSequenceLength = 0;
        for(int n : set) {
            if(set.contains(n-1)){
                continue;
            }

            int nextN = n + 1;
            int sequenceLength = 1;
            while(set.contains(nextN)) {
                sequenceLength++;
                nextN++;
            }
            maxSequenceLength = Math.max(maxSequenceLength, sequenceLength);
        }
        return maxSequenceLength;
    }
}
```

## Complexity

- Time: O(n)
- Space: O(n)

## Gotcha

just check if the number is the start of the sequence by checking if n-1 is present or not then proceed to check the length of sequence
