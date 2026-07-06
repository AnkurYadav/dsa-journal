# LC 143 - reorder-list

**Difficulty:** Medium
**Pattern:** linked list, two pointers
**Link:** https://leetcode.com/problems/reorder-list

## Approach

First find the mid of the linked list, then split and reverse the second half of the list then merge the two lists alternatively

## Code

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public void reorderList(ListNode head) {
        if(head.next == null) {
            return;
        }

        // find mid
        ListNode fast = head;
        ListNode prevSlow = null;
        ListNode slow = head;
        while(fast != null && fast.next != null) {
            fast = fast.next.next;
            prevSlow = slow;
            slow = slow.next;
        }

        prevSlow.next = null;
        ListNode mid = slow;

        // reverse second half
        ListNode prev = null;
        ListNode curr = mid;
        while(curr != null) {
            ListNode next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }

        ListNode revHead = prev;

        // merge
        ListNode n1 = head;
        ListNode n2 = revHead;
        while(n1 != null && n2 != null) {
            ListNode n1Next = n1.next;
            n1.next = n2;
            ListNode n2Next = n2.next;
            if(n1Next != null) {
                n2.next = n1Next;
            }
            n1 = n1Next;
            n2 = n2Next;
        }
    }
}
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

keep in mind and handle the edge cases
