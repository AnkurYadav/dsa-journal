# LC 121 - best-time-to-buy-and-sell-stock

**Difficulty:** Easy
**Pattern:** two pointers
**Link:** https://leetcode.com/problems/best-time-to-buy-and-sell-stock

## Approach

use two pointers to keep track of min price till date using left pointer and compute diff with larger price on right to calculate max_profit,
since we need min_price till date to maximize our profit, so we use left pointer to track that and then we calculate profit by moving right pointer and comparing with max_profit

## Code

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        l = len(prices)
        i = 0
        j = 1
        max_diff = 0
        while i < j and j < l:
            if prices[i] > prices[j]:
                i = j
            elif prices[i] < prices[j]:
                diff = prices[j] - prices[i]
                if diff > max_diff:
                    max_diff = diff
            j = j+1

        return max_diff
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

use two pointers to keep track of min till date and calculate profits
