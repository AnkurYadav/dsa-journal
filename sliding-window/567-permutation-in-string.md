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

```java
class Solution {
    public boolean checkInclusion(String s1, String s2) {
        int l_s1 = s1.length();
        int l_s2 = s2.length();

        Map<Character, Integer> map = new HashMap<>();
        for(int i = 0; i < l_s1; i++) {
            char ch = s1.charAt(i);
            if(map.containsKey(ch)) {
                map.put(ch, map.get(ch)+1);
            }
            else {
                map.put(ch, 1);
            }
        }

        int lo = 0;
        int hi = 0;
        while(lo <= hi && hi < l_s2) {
            char ch_hi = s2.charAt(hi);
            if(map.containsKey(ch_hi)) {
                int count = map.get(ch_hi);
                if(count == 1) {
                    map.remove(ch_hi);
                }
                else {
                    map.put(ch_hi, map.get(ch_hi)-1);
                }
                if(hi-lo+1 == l_s1){
                    return true;
                }
                hi++;
            }
            else{
                if(hi == lo) {
                    hi++;
                    lo++;
                    continue;
                }

                char ch_lo = s2.charAt(lo);
                if(map.containsKey(ch_lo)) {
                    map.put(ch_lo, map.get(ch_lo)+1);
                }
                else {
                    map.put(ch_lo, 1);
                }
                lo++;
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

- You can use single hashmap, just decrease the frequency when you add a new character in substring, and increase the frequency if you remove a character
- if character is not in hashmap is treated differently than a character which is present in hasmap but is exhausted
