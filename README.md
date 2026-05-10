# DSA Journal

My systematic walk through data structures and algorithms - one problem a day, every day.

Started **2026-05-10**. Working through [NeetCode 150](https://neetcode.io/practice), then expanding to company-tagged sets. Solutions in **Python 3**.

---

## Why this repo exists

1. **Spaced retention.** Solving without writing it down is solving without remembering. Each problem here gets a short note covering pattern, approach, and the one gotcha I'd forget in 3 months.
2. **Visible consistency.** The commit graph is the receipt that I show up.
3. **Searchable reference.** When I see "this looks like a sliding window problem", I want to grep my own notes first.

---

## Structure

Folders follow the [NeetCode 150](https://neetcode.io/practice) pattern groups:

```
arrays-hashing/
two-pointers/
sliding-window/
stack/
binary-search/
linked-list/
trees/
tries/
heap-priority-queue/
backtracking/
graphs/
advanced-graphs/
dp-1d/
dp-2d/
greedy/
intervals/
math-geometry/
bit-manipulation/

_template.md       ← copy this for every new problem
needs-review.md    ← list of problems that took >12 min, revisit weekly
```

Each problem file is named `<lc-number>-<slug>.md` (e.g. `001-two-sum.md`).

---

## Per-problem template

Every file follows this structure (see `_template.md`):

```markdown
# LC <number> - <problem name>

**Difficulty:** Easy | Medium | Hard
**Pattern:** <e.g. sliding window, monotonic stack, two pointers>
**Link:** https://leetcode.com/problems/...

## Approach
<3–5 sentences. The intuition before the code.>

## Code
```python
def solve(...):
    ...
```

## Complexity
- Time: O(...)
- Space: O(...)

## Gotcha
<the one thing I'd forget if I came back to this cold>
```

---

## Progress

| Pattern | Solved | NeetCode 150 |
|---|:---:|:---:|
| Arrays & Hashing | 0 | 9 |
| Two Pointers | 0 | 5 |
| Sliding Window | 0 | 6 |
| Stack | 0 | 7 |
| Binary Search | 0 | 7 |
| Linked List | 0 | 11 |
| Trees | 0 | 15 |
| Tries | 0 | 3 |
| Heap / Priority Queue | 0 | 7 |
| Backtracking | 0 | 9 |
| Graphs | 0 | 13 |
| Advanced Graphs | 0 | 6 |
| 1-D DP | 0 | 12 |
| 2-D DP | 0 | 11 |
| Greedy | 0 | 8 |
| Intervals | 0 | 6 |
| Math & Geometry | 0 | 8 |
| Bit Manipulation | 0 | 7 |
| **Total** | **0** | **150** |

Updated weekly on Sundays.

---

## Language choice

Python 3 for conciseness. The standard library (`heapq`, `collections.deque`, `defaultdict`, `Counter`, `bisect`, `itertools`, `functools.cache`) makes interview-style problems readable. I write production code in TypeScript / Node.js - Python is the right tool for *this* job.

---

## How I work through problems

1. Read the problem twice. State it back in my own words.
2. Plan on paper for ≤5 min - pattern? data structure? edge cases?
3. Code it. No editor autocomplete tricks.
4. Run against the examples. Fix.
5. **Read the editorial** even when my solution passed - there's almost always a sharper take.
6. Write the note (this file) - I treat this as part of solving, not after.
7. Re-implement from scratch the next morning if it took >20 min.

---

## Attribution & license

- Problem statements © [LeetCode](https://leetcode.com).
- My code: [MIT](LICENSE-CODE).
- My notes: [CC BY 4.0](LICENSE-NOTES).
