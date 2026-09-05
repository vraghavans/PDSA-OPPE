# Q003 — BestFare

## Student Question

An airlines company has flights operational in `n` cities labeled `0` to `n-1`. Write a function **`best_fare(flight_route, source, destination, k)`** in which you are given a weighted adjacency list `flight_route` in the following format:

```text
flight_route = {
    source_index : [(destination_index, price), (destination_index, price), ...],
    ...
    source_index : [(destination_index, price), (destination_index, price), ...]
}
```

You are also given three integers `source`, `destination` and `k` (positive integer), function returns minimum cost and flight route in the format `(minimum_cost, [source, next_stop, next_stop, ..., destination])` from `source` to `destination` with at most `k` stops in between (`source` and `destination` are not included). If there is no such route, then return string `Not found`.

![BestFare graph](best_fare_graph.png)

### Student Function

Implement the following function:

```python
def best_fare(flight_route, source, destination, k):
```

The original source does not contain a `YOUR CODE HERE` marker for this implementation question, so no artificial fill-in marker is added here.

### Sample Input 1

```text
5
[(0,1,1000),(0,2,500),(0,3,3000),(2,0,2000),(2,1,3000),(1,3,300),(3,4,600),(2,4,2000)]
0
4
1
```

### Output

```text
(2500, [0, 2, 4])
```

### Sample Input 2

```text
5
[(0,1,1000),(0,2,500),(0,3,3000),(2,0,2000),(2,1,3000),(1,3,300),(3,4,600),(2,4,2000)]
0
4
0
```

### Output

```text
Not found
```

## Full Reference Code

```python
def addallpath(WList,u, d, visited, path,allpath):
  visited[u]= True
  path.append(u)
  if u == d:
         L = path.copy()
         allpath.append(L)
  else:
      for i in WList[u]:
          if visited[i[0]]== False:
              addallpath(WList, i[0], d, visited, path, allpath)
  path.pop()
  visited[u]= False

# Following function returns a list of all paths from s to d
# Format of returned list:- [[s,...,d],[s,...,d],...]
def findallpath(WList,s,d):
    visited = {}
    allpath = []
    for v in WList.keys():
        visited[v] = False
    path = []
    addallpath(WList,s, d, visited, path,allpath)
    return(allpath)
def best_fare(flight_route, source, destination, k):
    L = findallpath(flight_route, source, destination)
    if L != []:
        cost = 1 + len(flight_route.keys()) * max([d for u in flight_route.keys() for (v, d) in flight_route[u]])
        route = []
        for pth in L:
            if len(pth) < k + 3:
                s = 0
                for i in range(0, len(pth) - 1):
                    for j in flight_route[pth[i]]:
                        if pth[i + 1] == j[0]:
                            s += j[1]
                if s < cost:
                    cost = s
                    route = pth
        if route != []:
            return (cost, route)
        else:
            return 'Not found'
    else:
        return 'Not found'

size = int(input())
edges = eval(input())
s = int(input())
d = int(input())
k = int(input())
WL = {}
for i in range(size):
    WL[i] = []
for ed in edges:
    WL[ed[0]].append((ed[1],ed[2]))
print(best_fare(WL,s,d,k))
```

## Source / Occurrence Metadata

- Original question ID: `W5LCP3 — BestFare`
- Source: `PDSA OPPE1/iitm-pdsa-main/LiveCoding/Week-5/W5LCP3-BestFare.md`
- Original source images:
  - `https://github.com/nelsondsouza/iitm-pdsa/assets/19646977/5a793c12-5ec7-43ab-8b4d-96b3ce81ed79`
  - `https://github.com/nelsondsouza/iitm-pdsa/assets/19646977/8bf853e9-5a8e-4e0c-9567-592f13d6e687`
- Student-facing image: `best_fare_graph.png` — cropped from the supplied source screenshot to retain only the graph visual.
- Occurrences currently confirmed: 1; final occurrence count must be updated after the complete OPPE1/OPPE2/OPPE3 repository scan.
- Deduplication note: the graph diagram is part of the student-facing question and must be preserved. Its contents were extracted for validation/deduplication, but the extracted node/edge list is not substituted for the diagram in the student-facing section.
