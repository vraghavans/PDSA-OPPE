# Q018 — Find Number of Occurrence in Unsorted List

## Student Question

Find Number of Occurrence

Write a function findOccurrence(L,k) that accepts an unsorted list L of integers and an integer k.
The function returns the total number of occurrences of k in the list L. If k is not present in the list then return -1.
Write an efficient solution of complexity O(n)

**Sample Input**
```text
[1,1,1,1,2,2,2,2,3,3,3,3,3,3,4,4,4,3,3,3]
3
```
**Sample Output**
```text
9
```

### Student Function
```python
def findOccurrence(L, k):
```

## Full Reference Code
```python
def findOccurrence(L, k):
    count = 0
    for num in L:
        if num == k:
            count += 1
    if count == 0:
        return -1
    return count
```

## Source / Occurrence Metadata
- Sources: `PDSA OPPE1/iitm-pdsa-main/OPE/findOccurrence-2.py`; `PDSA OPPE1/iitm-pdsa-main/OPE/findOccurrenceInUnsortedList.py`
- Occurrences currently confirmed: 2.
- Deduplication note: the two files contain the same student-facing task and constraints; the source implementations differ, so both are retained in source metadata.
