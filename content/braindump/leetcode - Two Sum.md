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

- I'll iterate through the list once.
- For each number, I'll compute the `need = target - num.`
- If need already exists in seen, that means i have found the answer.
- Otherwise, i store the current number with its index in seen.

#### Complexity
- Time: O(n)
- Space: O(n)