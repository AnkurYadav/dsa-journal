# LC 121 - best-time-to-buy-and-sell-stock

**Difficulty:** Easy
**Pattern:** two pointers, sliding window
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

```java
class Solution {
    public int maxProfit(int[] prices) {
        int l = prices.length;
        int i = 0;
        int j = 1;
        int maxProfit = 0;
        while(i < j && j < l) {
            if(prices[j] < prices[i]) {
                i = j;
                j++;
                continue;
            }

            int profit = prices[j] - prices[i];
            if(profit > maxProfit) {
                maxProfit = profit;
            }

            j++;
        }

        return maxProfit;
    }
}
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

use two pointers to keep track of min till date and calculate profits
