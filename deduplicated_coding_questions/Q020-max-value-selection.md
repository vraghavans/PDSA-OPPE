# Q020 — MaxvalueSelection

## Student Question

Write a function MaxvalueSelection(items, C) that accepts a dictionary items where each key of the dictionary represents the item name and the corresponding value is a tuple (number of units, value of all units) and function accept one more variable c which represents the maximum capacity of units you can select from all items to get maximum value.

**Sample input**
```text
{1:(10,60),2:(20,100),3:(30,120)}
```

**Output**
```text
240
```

### Student Function
```python
def MaxvalueSelection(items, C):
```

## Full Reference Code
```python
def MaxvalueSelection(items, C):
    items_list = [(weight, value / weight) for weight, value in items.values()]
    items_list.sort(key=lambda x: x[1], reverse=True)
    total_value = 0
    remaining_capacity = C
    for weight, value_per_unit in items_list:
        units_to_add = min(weight, remaining_capacity)
        total_value += units_to_add * value_per_unit
        remaining_capacity -= units_to_add
    return int(total_value)
```

## Source / Occurrence Metadata
- Source: `PDSA OPPE1/iitm-pdsa-main/OPE/maxValueSelection.py`
- Occurrences currently confirmed: 1; final count subject to remaining OPPE2/OPPE3 scan.
- Related image-based source: `graphForMaxValueSelection.py` contains a plotting variant of the same function, but the essential question is already represented here; image-backed variants remain subject to later image extraction.
