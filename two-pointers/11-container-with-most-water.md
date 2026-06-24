# LC 11 - container-with-most-water

**Difficulty:** Medium
**Pattern:** two pointers
**Link:** https://leetcode.com/problems/container-with-most-water

## Approach

Start with widest area possible then move inwards exclding the shorter height in hope to find a greater height so that area is increased

## Code

```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        l = len(height)
        i = 0
        j = l-1
        max_area = 0
        while i < j:
            if height[i] < height[j]:
                curr_area = (j-i) * height[i]
                i+=1
            else:
                curr_area = (j-i) * height[j]
                j-=1
            
            max_area = max(max_area, curr_area)
        
        return max_area

```

```java
class Solution {
    public int maxArea(int[] height) {
        int i = 0;
        int j = height.length - 1;

        int maxArea = 0;

        while(i < j) {
            int area = 0;
            if(height[i] < height[j]) {
                area = height[i] * (j - i);
                i++;
            }
            else {
                area = height[j] * (j - i);
                j--;
            }

            maxArea = Math.max(area, maxArea);
        }

        return maxArea;
    }
}
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

Move shorter pointer inward
