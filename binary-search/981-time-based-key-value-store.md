# LC 981 - time-based-key-value-store

**Difficulty:** Medium
**Pattern:** map, binary search
**Link:** https://leetcode.com/problems/time-based-key-value-store

## Approach

Store the data in map with key -> key, value -> List<timestamp,value> or binarySearchTree<timestamp,value>, then binary search on list to find timestamp equal or lower than provide one.

## Code

1. using built int treeMap library for binary search
```java
class TimeMap {
    private Map<String, TreeMap<Integer, String>> map;

    public TimeMap() {
        this.map = new HashMap<>();
    }
    
    public void set(String key, String value, int timestamp) {
        this.map.computeIfAbsent(key, k -> new TreeMap()).put(timestamp, value);
    }
    
    public String get(String key, int timestamp) {
        if(this.map.containsKey(key)) {
            Map.Entry<Integer, String> entry = this.map.get(key).floorEntry(timestamp);
            if(entry != null) {
                return entry.getValue();
            }
        }

        return "";
    }
}

/**
 * Your TimeMap object will be instantiated and called as such:
 * TimeMap obj = new TimeMap();
 * obj.set(key,value,timestamp);
 * String param_2 = obj.get(key,timestamp);
 */
```

2. using custom binary serach on sorted list
```java
class Node {
    public int timestamp;
    public String value;

    public Node(int timestamp, String value) {
        this.timestamp = timestamp;
        this.value = value;
    }
}

class TimeMap {
    private Map<String, List<Node>> map;

    public TimeMap() {
        this.map = new HashMap<>();
    }
    
    public void set(String key, String value, int timestamp) {
        this.map.computeIfAbsent(key, k -> new ArrayList()).add(new Node(timestamp, value));
    }
    
    public String get(String key, int timestamp) {
        if(this.map.containsKey(key)) {
            List<Node> list = this.map.get(key);
            
            int lo = 0;
            int hi = list.size() - 1;
            int resInd = -1;
            while(lo <= hi) {
                int mid = lo + ((hi-lo)/2);
                Node midNode = list.get(mid);

                if(midNode.timestamp <= timestamp) {
                    resInd = mid;
                    lo = mid + 1;
                }
                else {
                    hi = mid - 1;
                }
            }

            if(resInd > -1 && resInd < list.size()) {
                Node node = list.get(resInd);
                if(node.timestamp <= timestamp) {
                    return node.value;
                }
            }
        }

        return "";
    }
}

/**
 * Your TimeMap object will be instantiated and called as such:
 * TimeMap obj = new TimeMap();
 * obj.set(key,value,timestamp);
 * String param_2 = obj.get(key,timestamp);
 */
```

## Complexity

- Time: O(log(n))
- Space: O(n)

## Gotcha

Can use binary search since timestamps are said to be already sorted
