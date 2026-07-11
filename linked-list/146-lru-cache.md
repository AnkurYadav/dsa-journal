# LC 146 - lru-cache

**Difficulty:** Medium
**Pattern:** linked list, hash map
**Link:** https://leetcode.com/problems/lru-cache

## Approach

Use hash map to quickly find the key, use doubly linked list to quickly reorder the nodes according to latest access order.

## Code

```java
class Node {
    public int key;
    public int value;
    public Node next;
    public Node prev;

    public Node(int key, int value) {
        this.key = key;
        this.value = value;
        this.next = null;
        this.prev = null;
    }
}

class LRUCache {
    private int capacity;
    private int length;
    private Map<Integer, Node> map;
    private Node head;
    private Node tail;

    public LRUCache(int capacity) {
        this.capacity = capacity;
        this.length = 0;
        this.map = new HashMap<>();
        this.head = null;
        this.tail = null;
    }
    
    public int get(int key) {
        if(this.map.containsKey(key)) {
            Node node = this.map.get(key);
            if(node != head){
                node.prev.next = node.next;
                if(node.next != null) {
                    node.next.prev = node.prev;
                }
                else {
                    this.tail = node.prev;
                }
                node.prev = null;
                node.next = this.head;
                this.head.prev = node;
                this.head = node;
            }
            return node.value;
        }
        return -1;
    }
    
    public void put(int key, int value) {
        if(map.containsKey(key)) {
            Node node = this.map.get(key);
            node.value = value;
            if(node != head){
                node.prev.next = node.next;
                if(node.next != null) {
                    node.next.prev = node.prev;
                }
                else {
                    this.tail = node.prev;
                }
                node.prev = null;
                node.next = this.head;
                this.head.prev = node;
                this.head = node;
            }
        }
        else {
            Node newNode = new Node(key, value);
            this.map.put(key, newNode);
            if(this.head == null) {
                this.head = newNode;
                this.tail = newNode;
            }
            else {
                if(this.length == this.capacity) {
                    Node nodeToRemove = this.tail;
                    this.map.remove(nodeToRemove.key);
                    this.tail = nodeToRemove.prev;
                    if(this.tail != null) {
                        this.tail.next = null;
                    }
                    nodeToRemove.prev = null;
                    this.length--;
                }
                newNode.next = this.head;
                this.head.prev = newNode;
                this.head = newNode;
                if(this.tail == null) {
                    this.tail = newNode;
                }
            }
            this.length++;
        }
    }
}

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache obj = new LRUCache(capacity);
 * int param_1 = obj.get(key);
 * obj.put(key,value);
 */
```

## Complexity

- Time: O(1)
- Space: O(n)

## Gotcha

Use doubly linked list for keeping track of access order in O(1)
