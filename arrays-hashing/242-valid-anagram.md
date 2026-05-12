# LC 242 - valid-anagram

**Difficulty:** Easy
**Pattern:** hashset/dictionary
**Link:** https://leetcode.com/problems/valid-anagram

## Approach

Store the character and count in dictionary for first string and check if the count matches for second string

## Code

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # if string lengths are not equal
        if len(s) != len(t):
            return False

        # create dictionary to keep character count in string s
        char_dict = {}
        for ch in s:
            if ch in char_dict:
                char_dict[ch] += 1
            else:
                char_dict[ch] = 1

        # for each character in string t remove one count from dictionary
        for ch in t:
            if ch in char_dict:
                char_dict[ch] -= 1
                if char_dict[ch] < 0:
                    return False
            else:
                return False

        # if any character count still is non-zero then not an anagram
        for ch in char_dict:
            if char_dict[ch] != 0:
                return False
        
        return True
```

## Complexity

- Time: O(n)
- Space: O(n)

## Gotcha

early check for size mismatch
