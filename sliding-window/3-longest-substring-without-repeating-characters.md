# LC 3 - longest-substring-without-repeating-characters

**Difficulty:** Medium
**Pattern:** sliding window, hash table
**Link:** https://leetcode.com/problems/longest-substring-without-repeating-characters

## Approach

use slidingWindow with two pointers to always keep substring without any repeating characters and increase the length if any repeating character is found move left pointer to remove first occurance of duplicate

## Code

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        l = len(s)
        # handle corner cases
        if l == 0:
            return 0
        elif l == 1:
            return 1
        
        dup_hash = {}
        i = 0
        j = 1
        dup_hash[s[i]] = i
        max_len = 1
        while i < j and j < l:
            if s[j] in dup_hash:
                # calculate and compare max
                max_len = max(max_len, j - i)
                next_i = dup_hash[s[j]] + 1
                # remove all not included chars
                for k in range(i, next_i):
                    del dup_hash[s[k]]
                i = next_i
            dup_hash[s[j]] = j
            j += 1
        # calculate if loop breaks becaues of string end
        max_len = max(max_len, j - i)

        return max_len
```

## Complexity

- Time: O(n)
- Space: O(n)

## Gotcha

remove not included chars in current substring window from hash table
