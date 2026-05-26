# LC 567 - permutation-in-string

**Difficulty:** Medium
**Pattern:** sliding window, hashmap
**Link:** https://leetcode.com/problems/permutation-in-string

## Approach

Use sliding window to check if the new substring has same characters as first string, if not update the window

## Code

```python
class Solution:
    def checkInclusion(self, s1: str, s2: str) -> bool:
        l1 = len(s1)
        l2 = len(s2)
        if l1 > l2:
            return False
        
        freq_dict_s1 = {}
        for ch in s1:
            if ch in freq_dict_s1:
                freq_dict_s1[ch] += 1
            else:
                freq_dict_s1[ch] = 1

        i=0
        j=0
        while i<=j and j<l2:
            if j - i == l1:
                break
            ch = s2[j]
            if ch not in freq_dict_s1:
                for i in range(i,j):
                    freq_dict_s1[s2[i]] += 1
                i += 1
                j=i
            elif freq_dict_s1[ch] > 0:
                freq_dict_s1[ch] -= 1
                j += 1
            else:
                freq_dict_s1[s2[i]] += 1
                i += 1

        for ch in freq_dict_s1:
            if freq_dict_s1[ch] > 0:
                return False

        return True
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

- You can use single hashmap, just decrease the frequency when you add a new character in substring, and increase the frequency if you remove a character
- if character is not in hashmap is treated differently than a character which is present in hasmap but is exhausted
