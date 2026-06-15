# LC 125 - valid-palindrome

**Difficulty:** Easy
**Pattern:** two pointers, string
**Link:** https://leetcode.com/problems/valid-palindrome

## Approach

check only alphanumeric characters using two pointers for equality ignore others

## Code

```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        i = 0
        j = len(s) - 1

        s = s.lower()

        while i < j:
            ch_i = s[i]
            ch_j = s[j]

            if not self.isAlphanum(ch_i):
                i += 1
                continue
            if not self.isAlphanum(ch_j):
                j -= 1
                continue

            if ch_i != ch_j:
                return False
            
            i += 1
            j -= 1

        return True


    def isAlphanum(self, ch: str) -> bool:
        val_ch = ord(ch)
        if (48 <= val_ch <=57) or (97 <= val_ch <= 122):
            return True
        return False
```

```java
class Solution {
    public boolean isPalindrome(String s) {
        int i = 0;
        int j = s.length() -1;

        while(i < j) {
            char c_i = s.charAt(i);
            char c_j = s.charAt(j);

            if(!Character.isLetterOrDigit(c_i)) {
                i++;
                continue;
            }
            if(!Character.isLetterOrDigit(c_j)) {
                j--;
                continue;
            }

            if(Character.toLowerCase(c_i) != Character.toLowerCase(c_j)) {
                return false;
            }

            i++;
            j--;
        }

        return true;
    }
}
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

- ascii codes for alphanumerics
- use two pointers
- just ignore non-alphanumerics to save space
