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

## Complexity

- Time: O(nlogk)
- Space: O(n)

## Gotcha

use heap to get the largest k elements in O(nlogk)
