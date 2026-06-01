
# LC 21 - merge-two-sorted-lists

**Difficulty:** Easy
**Pattern:** linked lists
**Link:** https://leetcode.com/problems/merge-two-sorted-lists

## Approach

one pointer at first list another pointer at second list compare the values at the pointer add to the new list if lesser increase the pointer

## Code

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        if list1 is None:
            return list2
        elif list2 is None:
            return list1

        mergedList = None
        mergeListCurr = None
        list1Curr = list1
        list2Curr = list2

        if list1Curr.val < list2Curr.val:
            mergeListCurr = list1Curr
            list1Curr = list1Curr.next
        else:
            mergeListCurr = list2Curr
            list2Curr = list2Curr.next
        
        mergedList = mergeListCurr

        while list1Curr is not None and list2Curr is not None:
            if list1Curr.val < list2Curr.val:
                mergeListCurr.next = list1Curr
                list1Curr = list1Curr.next
            else:
                mergeListCurr.next = list2Curr
                list2Curr = list2Curr.next
            mergeListCurr = mergeListCurr.next
        
        if list1Curr is None:
            mergeListCurr.next = list2Curr
        elif list2Curr is None:
            mergeListCurr.next = list1Curr

        return mergedList
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

check if the list finished early move the next list completely to new list
