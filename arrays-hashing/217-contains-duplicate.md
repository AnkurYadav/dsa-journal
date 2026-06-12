# LC 217 - contains-duplicate

**Difficulty:** Easy
**Pattern:** hashing
**Link:** https://leetcode.com/problems/contains-duplicate/

## Approach

create hashset to check if any value is already in the hashset

## Code

```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        hash_set = set()
        for i in nums:
            if i in hash_set:
                return True
            hash_set.add(i)
        return False
```

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> set = new HashSet<>();

        for(int n : nums) {
            if(set.contains(n)){
                return true;
            }
            else {
                set.add(n);
            }
        }

        return false;
    }
}
```

## Complexity

- Time: O(n)
- Space: O(n)

## Gotcha

none
