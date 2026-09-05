# Q001 — Findpeak

## Concept
Peak finding / binary search

## Statement
> Write a function  `Findpeak(L)`  that accepts a list L of  `n`  distinct elements and returns the peak element of the list. A list element is a peak if it is greater than its neighbors. For corner elements, we need to consider only one neighbor. Write an efficient solution of O(logn) complexity. Consider that there is only one peak is in the list, L.

## Sample Input 1
```text
[5, 10, 20, 15]
```

## Output 1
```text
20
```

## Sample Input 2
```text
[1,2,3,4,5,6,7,8]
```

## Output 2
```text
8
```

## Boilerplate / Student-Fill Template

The source contains a complete reference implementation rather than an explicit `YOUR CODE` marker. For the OPPE app, the student-facing version should expose the required function and mark the implementation area explicitly:

```python
def Findpeak(L):
    # YOUR CODE
    pass
```

**Important:** The `YOUR CODE` block above is an app-facing extraction of the student-fill area. It is not claimed to be an exact marker present in the source file.

## Full Reference Code

The complete code from the source is retained here for evaluator/reference use:

```python
def findPeakUtil(arr, low, high, n):
    mid = low + (high - low) // 2
    mid = int(mid)
    
    if ((mid == 0 or arr[mid - 1] < arr[mid]) and (mid == n - 1 or arr[mid + 1] < arr[mid])):
        return arr[mid]
    elif (mid > 0 and arr[mid - 1] > arr[mid]):
        return findPeakUtil(arr, low, (mid - 1), n)
    else:
        return findPeakUtil(arr, (mid + 1), high, n)

def Findpeak(L):
    n = len(L)
    return findPeakUtil(L, 0, n - 1, n)
```

## Constraints / Relevant Information
- The list contains `n` distinct elements.
- There is exactly one peak in the list.
- The required time complexity is O(log n).
- For corner elements, only one neighbor is considered.

## Occurrence Count
1 (currently recorded; final count will be updated after the complete repository scan)

## Source
`PDSA OPPE1/iitm-pdsa-main/LiveCoding/Week-2/W2LCP1-FindPeak.md`
