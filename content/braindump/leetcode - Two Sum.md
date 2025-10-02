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