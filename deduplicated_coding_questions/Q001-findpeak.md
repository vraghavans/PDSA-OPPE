# Q001 — Findpeak

## Concept
Peak finding / binary search

## Statement
> Write a function  `Findpeak(L)`  that accepts a list L of  `n`  distinct elements and returns the peak element of the list. A list element is a peak if it is greater than its neighbors. For corner elements, we need to consider only one neighbor. Write an efficient solution of O(logn) complexity. Consider that there is only one peak is in the list, L.

## Inputs
**Sample Input 1**
```text
[5, 10, 20, 15]
```

**Sample Input 2**
```text
[1,2,3,4,5,6,7,8]
```

## Outputs
**Output 1**
```text
20
```

**Output 2**
```text
8
```

## Boilerplate Code — Student Version

The student receives the **full runnable program structure**, with the implementation portion replaced by a clearly marked `YOUR CODE HERE` block. The boilerplate is intentionally not reduced to only the function body.

```python
def findPeakUtil(arr, low, high, n):
    # YOUR CODE HERE
    pass

def Findpeak(L):
    n = len(L)
    return findPeakUtil(L, 0, n - 1, n)
```

> Note: The original source file contains the complete implementation but does not contain an explicit `YOUR CODE HERE` marker. The student version above marks the implementation region that must be supplied while preserving the original program structure and function signatures.

## Full Reference Code

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
- There is only one peak in the list.
- The required solution complexity is O(logn).
- For corner elements, only one neighbor is considered.

## Occurrence Count
1 (currently recorded; final count will be established during the complete repository scan)

## Source
`PDSA OPPE1/iitm-pdsa-main/LiveCoding/Week-2/W2LCP1-FindPeak.md`
