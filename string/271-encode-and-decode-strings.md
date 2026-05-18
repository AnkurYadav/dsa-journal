# LC 271 - encode-and-decode-strings

**Difficulty:** Medium
**Pattern:** string
**Link:** https://leetcode.com/problems/encode-and-decode-strings

## Approach

add length of string before the string and then add a separator to identify the length and string

## Code

```python
class Solution:
    """
    @param: strs: a list of strings
    @return: encodes a list of strings to a single string.
    """
    def encode(self, strs):
        res = ""
        for s in strs:
            res += str(len(s)) + ":" + s
        return res

    """
    @param: str: A string
    @return: decodes a single string to a list of strings
    """
    def decode(self, str):
        res = []
        i = 0
        while i < len(str):
            decodeStr = ""
            (strLen, start) = self.getStrLen(str, i)
            i = start + 1
            j = 0
            while j < strLen:
                decodeStr += str[i]
                j += 1
                i += 1
            res.append(decodeStr)
        return res

    def getStrLen(self, str, start):
        strLen = 0
        end = 0
        for i in range(start, len(str)):
            ch = str[i]
            if ch == ":":
                end = i
                break
            strLen = strLen * 10 + (ord(ch) - ord('0'))
        return (strLen, end)
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

use length of string as prefix to identify the string start and end
