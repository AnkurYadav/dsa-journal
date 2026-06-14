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

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        int length_s = s.length();
        int length_t = t.length();

        if(length_s != length_t) {
            return false;
        }

        Map<Character, Integer> map = new HashMap<>();

        for(int i = 0; i < length_s; i++) {
            char c = s.charAt(i);
            if(map.containsKey(c)) {
                int val = map.get(c);
                map.put(c, ++val);
            }
            else {
                map.put(c, 1);
            }
        }

        for(int i = 0; i < length_t; i++) {
            char c = t.charAt(i);
            if(map.containsKey(c)) {
                int val = map.get(c);
                if(val == 1) {
                    map.remove(c);
                }
                else{
                    map.put(c, --val);
                }
            }
            else {
                return false;
            }
        }
        
        return map.isEmpty();
    }
}
```

## Complexity

- Time: O(n)
- Space: O(n)

## Gotcha

early check for size mismatch
