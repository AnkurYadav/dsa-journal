# LC 19 - remove-nth-node-from-end-of-list

**Difficulty:** Medium
**Pattern:** linked list, two pointers
**Link:** https://leetcode.com/problems/remove-nth-node-from-end-of-list

## Approach

Use two pointers first pointer remains n steps ahead of second pointer so when first pointer reaches end of list second pointer is at the node before the nth node from end then we just reassign the next point to point to next to next node.

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
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode front = head;
        ListNode nFromFront = null;
        int count = 0;
        while(front != null) {
            front = front.next;
            count++;
            if(count == n+1){
                nFromFront = head;
            }
            if(count > n+1 && nFromFront != null) {
                nFromFront = nFromFront.next;
            }
        }


        if(nFromFront == null) {
            ListNode temp = head;
            head = head.next;
            temp.next = null;
        }
        else {
            ListNode temp = nFromFront.next;
            nFromFront.next = nFromFront.next.next;
            temp.next = null;
        }
        
        return head;
    }
}
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

Keep track of n = length of list since that's a edge case
