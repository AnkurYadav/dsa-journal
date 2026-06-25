# LC <number> - <problem name>

**Difficulty:** Medium
**Pattern:** array, hashSet
**Link:** https://leetcode.com/problems/valid-sudoku

## Approach

check if the numbers repeats in row, column, and subBox using hashSets

## Code

```python
class Solution:
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        rowDict = {}
        colDicts = [{}, {}, {}, {}, {}, {}, {}, {}, {}]
        boxDicts = [{}, {}, {}]

        for i in range(len(board)):
            rowDict = {}
            if i%3 == 0:
                boxDicts = [{}, {}, {}]
            row = board[i]
            for j in range(len(row)):
                n = row[j]
                if n == ".":
                    continue
                if n in rowDict:
                    return False
                rowDict[n] = True

                if n in colDicts[j]:
                    return False
                colDicts[j][n] = True

                boxNum = j//3
                if n in boxDicts[boxNum]:
                    return False
                boxDicts[boxNum][n] = True
        return True
```

```java
class Solution {
    public boolean isValidSudoku(char[][] board) {
        Set<String> set = new HashSet<>();
        
        for(int i = 0; i < board.length; i++) {
            for(int j = 0; j < board[i].length; j++) {
                if(board[i][j] != '.') {
                    String rowStr = "r"+i+board[i][j];
                    String colStr = "c"+j+board[i][j];
                    String boxStr = "b"+(i/3)+(j/3)+board[i][j];

                    if(set.contains(rowStr) || set.contains(colStr) || set.contains(boxStr)) {
                        return false;
                    }

                    set.add(rowStr);
                    set.add(colStr);
                    set.add(boxStr);
                }
            }
        }
        return true;
    }
}
```

## Complexity

- Time: O(n+m)
- Space: O(n*m)

## Gotcha

can use single hashset by encoding the row, column and box digits and check for repeatation like:
- '4' in row 7 is encoded as "(4)7".
- '4' in column 7 is encoded as "7(4)".
- '4' in the top-right block is encoded as "0(4)2".