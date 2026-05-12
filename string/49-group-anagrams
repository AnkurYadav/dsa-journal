# LC 49 - group-anagrams

**Difficulty:** Medium
**Pattern:** string
**Link:** https://leetcode.com/problems/group-anagrams

## Approach

sort each string and create a dictionary of sortedStrings and theier indices, later iterate the dictionary and create final array with anagrams together

## Code

```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        sorted_str_dict = {}
        for i in range(len(strs)):
            sorted_str = "".join(sorted(strs[i]))
            if sorted_str in sorted_str_dict:
                sorted_str_dict[sorted_str].append(i)
            else:
                sorted_str_dict[sorted_str] = [i]

        result = []
        for sorted_str in sorted_str_dict:
            anagram_index = sorted_str_dict[sorted_str]
            anagrams = []
            for i in anagram_index:
                anagrams.append(strs[i])
            result.append(anagrams)

        return result
```

## Complexity

- Time: O(n)
- Space: O(n)

## Gotcha

Sorting is ok since max length of each string is only 100, so no major extra work
