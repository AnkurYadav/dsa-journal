# LC 392 - is-subsequence

**Difficulty:** Easy
**Pattern:** string, two pointers
**Link:** https://leetcode.com/problems/is-subsequence

## Approach

- keep two pointers one at first string and second at second string
- compare first string's letters to second string's letters sequentially until one of them exhusts
- increase first pointer if letters match
- increase second pointer

## Code

```python
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        ls = len(s)
        lt = len(t)

        i = 0
        j = 0
        while i < ls and j < lt:
            if s[i] == t[j]:
                i+=1
            j+=1
            
        return i == ls
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

compare and skip non-matching in single go
