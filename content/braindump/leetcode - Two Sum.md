---
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
- Iterate through the list once.
- For each number, compute need = target - num
- If need already exists in seen, that means we have found the answer
- Otherwise, we
#### Complexity
- Time: O(n)
- Space: O(n)