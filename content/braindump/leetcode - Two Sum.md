---
title: Leetcode - Two Sum
tags:
  - leetcode
---
Link - https://leetcode.com/problems/two-sum/description/

```python
seen = {}
for i, num in enumerate(nums):
	need = target - num
	if need in seen:
		return [seen[need], i]
	seen[num] = i
```

#### Explains

- Traverse the list only once.
- For each element, compute `need = target - num`.
- If `need` already exists in `seen`, then both required values for the answer are found.
- Otherwise, store the current number in `seen` with its index.

#### Complexity

- Time: O(n) - each element is processed once.
- Space: O(n) - in the worst case, all elements are stored in `seen`.

