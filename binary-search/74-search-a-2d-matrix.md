# LC 74 - search-a-2d-matrix

**Difficulty:** Medium
**Pattern:** binary search
**Link:** https://leetcode.com/problems/search-a-2d-matrix

## Approach

two approaches:
1. first apply binary search to find the row then apply on the array to find the exact column
2. treat this matrix as a binary search tree rooted at the top-right corner and start from there to find the item

## Code

Row-column binary search:
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int start = 0;
        int end = matrix.length - 1;

        int rowIndex = -1;
        while(start <= end) {
            int rowMid = start + ((end-start)/2);

            if(target >= matrix[rowMid][0] && target <= matrix[rowMid][matrix[rowMid].length - 1]) {
                rowIndex = rowMid;
                break;
            }
            else if(target < matrix[rowMid][0]) {
                end = rowMid - 1;
            }
            else {
                start = rowMid + 1;
            }
        }

        if(rowIndex == -1) {
            return false;
        }

        start = 0;
        end = matrix[rowIndex].length - 1;

        while(start <= end) {
            int colMid = start + ((end - start)/2);

            if(matrix[rowIndex][colMid] == target) {
                return true;
            }
            else if(target < matrix[rowIndex][colMid]) {
                end = colMid - 1;
            }
            else {
                start = colMid + 1;
            }
        }

        return false;
    }
}
```

binary search tree:
```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) { 
        int root_row = 0;
        int root_col = matrix[root_row].length - 1;

        while(root_row < matrix.length && root_col >= 0) {
            if(target == matrix[root_row][root_col]) {
                return true;
            }
            else if(target < matrix[root_row][root_col]) {
                root_col--;
            }
            else {
                root_row++;
            }
        }

        return false;
    }
}
```

## Complexity

- Time: O(log(N*M))
- Space: O(1)

## Gotcha

this matrix can be treated as a binary search tree rooted at top-right corner
