# LC 138 - copy-list-with-random-pointer

**Difficulty:** Medium
**Pattern:** <e.g. sliding window, monotonic stack, two pointers>
**Link:** https://leetcode.com/problems/copy-list-with-random-pointer

## Approach

Keep track of corresponding new nodes for each old node in a map so that lookup is not costly then create linked list add corresponding nodes in map then again iterate over the list to assign random pointers.

## Code

```java
/*
// Definition for a Node.
class Node {
    int val;
    Node next;
    Node random;

    public Node(int val) {
        this.val = val;
        this.next = null;
        this.random = null;
    }
}
*/

class Solution {
    public Node copyRandomList(Node head) {
        if(head == null) {
            return head;
        }
        
        Map<Node, Node> map = new HashMap<>();

        Node headNew = new Node(head.val);

        Node currOld = head;
        Node currNew = headNew;
        while(currOld.next != null) {
            currNew.next = new Node(currOld.next.val);
            map.put(currOld, currNew);
            currOld = currOld.next;
            currNew = currNew.next;
        }
        // put last nodes
        map.put(currOld, currNew);

        currOld = head;
        currNew = headNew;
        while(currOld != null) {
            if(currOld.random != null) {
                currNew.random = map.get(currOld.random);
            }
            currOld = currOld.next;
            currNew = currNew.next;
        }

        return headNew;
    }
}
```

## Complexity

- Time: O(n)
- Space: O(n)

## Gotcha

- Keep in mind border conditions
- Keep track of last node
