# LC 347 - top-k-frequent-elements

**Difficulty:** Medium
**Pattern:** array, hashmap, heap, sort
**Link:** https://leetcode.com/problems/top-k-frequent-elements

## Approach

create frequency map and then sort it by frequency to get top k frequent elements list

## Code

```python
import heapq

class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        freq_dict_by_num = {}
        for i in nums:
            if i in freq_dict_by_num:
                freq_dict_by_num[i] += 1
            else:
                freq_dict_by_num[i] = 1

        freq_dict_by_freq = {}
        freq_arr = []
        for i in freq_dict_by_num:
            freq = freq_dict_by_num[i]
            freq_arr.append(freq)
            if freq in freq_dict_by_freq:
                freq_dict_by_freq[freq].append(i)
            else:
                freq_dict_by_freq[freq] = [i]

        k_largest = heapq.nlargest(k, freq_arr)
        res = []
        elements_remaining = k
        for freq in k_largest:
            elements = freq_dict_by_freq[freq]
            if len(elements) >= elements_remaining:
                res.extend(elements[0:elements_remaining])
                break
            else:
                res.extend(elements)
                elements_remaining -= len(elements)
            freq_dict_by_freq[freq] = []

        return res

```

```java
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        Map<Integer, Integer> frequencyMap = new HashMap<>();

        for(int n: nums) {
            int val = frequencyMap.computeIfAbsent(n, i -> 0);
            frequencyMap.put(n, ++val);
        }

        PriorityQueue<FrequencyItem> maxHeap = new PriorityQueue<>(Comparator.comparingInt(FrequencyItem::getFrequency).reversed());

        for(Map.Entry<Integer, Integer> entrySet: frequencyMap.entrySet()) {
            maxHeap.offer(new FrequencyItem(entrySet.getKey(), entrySet.getValue()));
        }

        int[] res = new int[k];
        for(int i = 0; i < k; i++) {
            res[i] = maxHeap.poll().getNum();
        }

        return res;
    }
}

class FrequencyItem {
    private int num;
    private int frequency;

    public FrequencyItem(int num, int frequency) {
        this.num = num;
        this.frequency = frequency;
    }

    public int getNum() {
        return this.num;
    }

    public int getFrequency() {
        return this.frequency;
    }
}
```

## Complexity

- Time: O(nlogk)
- Space: O(n)

## Gotcha

use heap to get the largest k elements in O(nlogk)
