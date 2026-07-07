# LC 2 - add-two-numbers

**Difficulty:** Medium
**Pattern:** linked list
**Link:** https://leetcode.com/problems/add-two-numbers

## Approach

go over the lists takings nodes one by one add them take only units place digit create a new node and keep track of carry

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode head = null;
        ListNode curr = null;

        int carry = 0;
        while(l1 != null || l2 != null) {
            int sum = carry;
            if(l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }
            if(l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }

            int unitPlace = sum % 10;
            carry = sum / 10;

            if(head == null) {
                head = new ListNode(unitPlace);
                curr = head;
            }
            else {
                curr.next = new ListNode(unitPlace);
                curr = curr.next;
            }
        }

        while(carry != 0) {
            int unitPlace = carry % 10;
            carry = carry / 10;
            curr.next = new ListNode(unitPlace);
            curr = curr.next;
        }

        return head;
    }
}
```

## Complexity

- Time: O(n)
- Space: O(1)

## Gotcha

1. Carry after the whole addition is done also needs to be handled
2. Single linked list when one is over also needs to be handled
