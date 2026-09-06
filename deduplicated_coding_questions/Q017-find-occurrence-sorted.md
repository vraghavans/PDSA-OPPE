# Q017 — Find Number of Occurrence in Sorted List

## Student Question

Find Number of Occurrence

Write a function findOccurrence(L,k) that accepts a sorted list L of integers and an integer k.
The function returns the total number of occurrences of k in the list L. If k is not present in the list then return -1.
Write an efficient solution of complexity O(logn)

Note: Do not use slicing in solution code for the list because it is O(n) operation.

**Sample Input**
```text
[1,1,1,1,2,2,2,2,3,3,3,3,3,3,4,4,4]
3
```
**Sample Output**
```text
6
```

### Student Function
```python
def findOccurrence(L, k):
```

## Full Reference Code
```python
def findOccurrence(L, k):
    left, right = 0, len(L) - 1
    first_occurrence = -1
    while left <= right:
        mid = left + (right - left) // 2
        if L[mid] == k:
            first_occurrence = mid
            right = mid - 1
        elif L[mid] < k:
            left = mid + 1
        else:
            right = mid - 1
    if first_occurrence == -1:
        return -1
    left, right = first_occurrence, len(L) - 1
    last_occurrence = first_occurrence
    while left <= right:
        mid = left + (right - left) // 2
        if L[mid] == k:
            last_occurrence = mid
            left = mid + 1
        else:
            right = mid - 1
    return last_occurrence - first_occurrence + 1
```

## Source / Occurrence Metadata
- Source: `PDSA OPPE1/iitm-pdsa-main/OPE/findOccurrence.py`
- Occurrences currently confirmed: 1; final count subject to remaining OPPE2/OPPE3 scan.
