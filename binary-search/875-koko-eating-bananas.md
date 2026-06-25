# LC 875 - koko-eating-bananas

**Difficulty:** Medium
**Pattern:** binary search
**Link:** https://leetcode.com/problems/koko-eating-bananas

## Approach

We need to search for min possible answer in the answer space [1,maxVal] such that the time taken to eat all the piles is <= H, use binary search to search for possible min answer.

## Code

```java
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        int max = piles[0];
        for(int b : piles) {
            max = Math.max(max, b);
        }

        int min = 1;
        int res = max;
        while(min <= max) {
            int k = min + ((max - min) / 2);
            int hours_needed = 0;
            for(int b : piles) {
                hours_needed += Math.ceil((double)b/k);
            }
            
            if(hours_needed <= h) {
                max = k - 1;
                res = k;
            }
            else {
                min = k + 1;
            }
        }

        return res;
    }
}
```

## Complexity

- Time: O(N * log(N))
- Space: O(1)

## Gotcha

we need the min answer among multiple possible ansers so binary serach for that in [1,maxVal]
