# Q025 — Tall Tower

## Student Question

Tall Tower

A tower is built using a combination of cylinders of different diameters and heights. We have to build a tall tower by placing one cylinder over another. The constraint is that in each adjacent pair of cylinder in tower, the top cylinder diameter should be less than or equal to the bottom cylinder diameter, and the volume of the top cylinder should be at most half the volume of the bottom cylinder. Each cylinder has a unique id starting from 0 to n-1, where n is the number of cylinders available.

Write a function tallTower(L) that accepts a list L of tuples and returns the maximum height achieved by stacking the cylinders. The tuples in the list L have the values (id, diameter, height).

Formula
Volume of cylinder = 3.14 * (Diameter/2)^2 * Height

**Sample input**
```text
[(0, 2, 2), (1, 3, 7), (2, 5, 6), (3, 1, 5), (4, 10, 1)]
```
**Sample Output** `9`

## Full Reference Code
```python
def tallTower(L):
    L.sort(key=lambda x: x[1], reverse=True)
    max_heights = [0] * len(L)
    for i in range(len(L)):
        curr_id, curr_diameter, curr_height = L[i]
        max_heights[curr_id] = curr_height
        for j in range(i):
            prev_id, prev_diameter, prev_height = L[j]
            if curr_diameter <= prev_diameter and curr_height <= prev_height * 0.5:
                max_heights[curr_id] = max(max_heights[curr_id], curr_height + max_heights[prev_id])
    return max(max_heights)
```

## Source / Occurrence Metadata
- Source: `PDSA OPPE1/iitm-pdsa-main/OPE/tallTower.py`
- Occurrences currently confirmed: 1; final count subject to remaining OPPE2/OPPE3 scan.
