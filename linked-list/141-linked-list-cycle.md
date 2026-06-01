# LC 141 - linked-list-cycle

**Difficulty:** Easy
**Pattern:** two pointers, linked list
**Link:** https://leetcode.com/problems/linked-list-cycle

## Approach

use two pointers slow and fast, slow moves one step and fast moves two steps if at any point slow and fast meets then there's cycle present other wise not

## Code

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: Optional[ListNode]) -> bool:
        slow = head
        fast = head

        while fast is not None and fast.next is not None:
            fast = fast.next.next
            slow = slow.next
            if slow == fast:
                return True
        
        return False
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

check for fast.next.next is null or not
