# Q026 — Teleport

## Student Question

Teleport

A sequence of n contiguous rooms are numbered from 0 to n-1 and are separated by locked doors. You do not have the key for any door. Initially you have no coin and are in room 0. Each room has a door to the next room which requires lock picking. It takes 1 hour to unlock the door by lock picking, and lock picking a door gets you one coin. Some rooms have an extra special door which leads to a room number greater than the current room number, which takes zero time but requires a number of coins equal to the number of rooms skipped (destination room number - current room number). One can always go to the next room by locking picking. You have to get to the last room in the least amount of time possible.

Write a function telteport(D) that returns the number of hours required to reach the last room for a given sequence of rooms. D is the dictionary such that key is the room number and the corresponding value is the special door destination. If key = value then the room does not have a special door.

**Example dictionary**
```text
{0: 0, 1: 1, 2: 2, 3: 5, 4: 4, 5: 5, 6: 9, 7: 8, 8: 8, 9: 9}
```

**Output** `7`

### Student Function
```python
def teleport(D):
```

## Full Reference Code
```python
def teleport(D):
    n = len(D)
    coins = 0
    hours = 0
    current_room = 0
    while current_room < n - 1:
        if D[current_room] > current_room + 1 and coins >= (D[current_room] - current_room - 1):
            coins -= (D[current_room] - current_room - 1)
            current_room = D[current_room]
        else:
            coins += 1
            hours += 1
            current_room += 1
    return hours
```

## Source / Occurrence Metadata
- Source: `PDSA OPPE1/iitm-pdsa-main/OPE/teleport.py`
- Occurrences currently confirmed: 1; final count subject to remaining OPPE2/OPPE3 scan.
