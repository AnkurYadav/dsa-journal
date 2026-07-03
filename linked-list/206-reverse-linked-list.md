# LC 206 - reverse-linked-list

**Difficulty:** Easy
**Pattern:** linked list
**Link:** https://leetcode.com/problems/reverse-linked-list

## Approach

maintain previous and current pointers and keep updating next pointer of current node to point to previous node

## Code

1. interative solution
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
    public ListNode reverseList(ListNode head) {
        ListNode prevNode = null;
        ListNode node = head;
        while(node != null) {
            ListNode nextNode = node.next;
            node.next = prevNode;
            prevNode = node;
            node = nextNode;
        }

        return prevNode;
    }
}
```

2. recursive solution
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
    public ListNode reverseList(ListNode head) {
        return reverse(null, head);
    }

    private ListNode reverse(ListNode prev, ListNode curr) {
        if(curr == null) {
            return prev;
        }

        ListNode next = curr.next;
        curr.next = prev;
        return reverse(curr, next);
    }
}
```

## Complexity

- Time: O(n)
- Space: O(1) -> iterative
         O(n) -> recursive (recursion stack)

## Gotcha

just need prev and curr pointers
