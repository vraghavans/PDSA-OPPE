# Q012 — Break Points

## Student Function

```python
def breakPoints(c, P):
```

The source file contains the implementation and sample calls but no separate prose question statement. The function sorts petrol-pump positions and returns the number of stops needed with tank capacity `c`, or `-1` if the destination cannot be reached.

**Sample calls**
```python
breakPoints(50, [0,10,80,100,260,250,230,220,120,140,180,30,40,20,300])  # 7
breakPoints(50, [0,51,100,140])  # -1
```

## Full Reference Code
```python
def breakPoints(c, P):
    P.sort()
    stops = 0
    fuel_left = c
    for i in range(1, len(P)):
        distance_to_next_pump = P[i] - P[i-1]
        if distance_to_next_pump > c:
            return -1
        if distance_to_next_pump > fuel_left:
            stops += 1
            fuel_left = c
        fuel_left -= distance_to_next_pump
    return stops
```

## Source / Occurrence Metadata
- Source: `PDSA OPPE1/iitm-pdsa-main/OPE/breakPoints.py`
- Occurrences currently confirmed: 1; final count subject to remaining OPPE2/OPPE3 scan.
