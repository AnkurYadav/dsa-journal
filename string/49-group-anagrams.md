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

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();

        for(String str: strs) {
            String encodedStr = encodeString(str);
            map.computeIfAbsent(encodedStr, k -> new ArrayList<>()).add(str);
        }

        List<List<String>> res = new ArrayList<>();
        for(List<String> value : map.values()) {
            res.add(value);
        }

        return res;
    }

    private String encodeString(String str) {
        int[] charCount = new int[26];

        for(int i = 0; i < str.length(); i++) {
            int ch_i = str.charAt(i) - 97;
            charCount[ch_i]++;
        }

        StringBuilder res = new StringBuilder("");
        for(int i = 0; i < 26; i++){
            if(charCount[i] > 0) {
                res.append((char) (i+97));
                res.append(charCount[i]);
            }
        }

        return res.toString();
    }
}
```

## Complexity

- Time: O(n)
- Space: O(n)

## Gotcha

Sorting is ok since max length of each string is only 100, so no major extra work
