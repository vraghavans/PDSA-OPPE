# Q015 — BST Comparison Count

## Student Question

Binary Search Tree Operation

Consider an implementation of a Binary Search Tree, where each node is created using the given class Node. Suppose it has a root variable that contains the reference to the root node of the binary search tree.

Write a function comparison_count(root, k) That accepts the reference of root node root of a non-empty binary search tree and an integer k. The function returns the number of comparisons during the search k in the binary search tree. Return (number of comparison, True) if k exists in BST, otherwise returns (number of comparison, False).

**Sample input 1**
```text
10 5 18 8 3 15 25 17
17
```
**Output**
```text
(4, True)
```

**Sample input 2**
```text
10 5 18 8 3 15 25 17
24
```
**Output**
```text
(3, False)
```

### Student Function
```python
def comparison_count(root, k):
```

## Full Reference Code
```python
def comparison_count(root, k):
    if root is None:
        return (0, False)
    comparisons = 0
    current = root
    while current is not None:
        comparisons += 1
        if k == current.data:
            return (comparisons, True)
        elif k < current.data:
            current = current.left
        else:
            current = current.right
    return (comparisons, False)
```

## Source / Occurrence Metadata
- Source: `PDSA OPPE1/iitm-pdsa-main/OPE/comparison_count.py`
- Occurrences currently confirmed: 1; final count subject to remaining OPPE2/OPPE3 scan.
