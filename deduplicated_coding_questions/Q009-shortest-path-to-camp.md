# Q009 — Shortest Path to Camp

## Student Question

Lost in the Jungle

Once upon a time, there was a group of adventurous friends who decided to go on a jungle expedition. They were exploring the dense, uncharted jungles of “Mystica’. While enjoying their journey, they realized they had lost their way back to the camp. The jungle was like a maze with various interconnected paths, and the friends had a map that displayed some landmarks and the connections between them. Each landmark was represented by a unique integer identifier, and they knew that the connections were bidirectional.

Write a function shortest_path_to_camp(totai_landmarks, connections, current_landmark, camp_landmark) that takes the following parameters:
- total_landmarks: An integer n, represents the total number of landmarks in the jungle labelled from 1 to n.
- connections: A dictionary which represents the adjacency list of connections, where each key represents the source landmark and values represent the list of adjacent landmarks of the source landmark.
- current_landmark: An integer, the current landmark where the friends are currently located.
- camp_ landmark: An integer, the landmark of their camp.

The function should return the minimum number of landmarks the friends need to cross to reach their camp (including current landmark and camp landmark).

**Sample input**
```text
18
(1:(2),2211,3,4],3:(2,5],4:(2,6},5: (3,9) ,6:14,7],7: (6,8) ,8: (7,9],9: (5,8],10:18]}
3
9
```

**Sample Output**
```text
3
```

### Student Function

```python
def shortest_path_to_camp(total_landmarks, connections, current_landmark, camp_landmark):
```

## Full Reference Code

```python
from collections import deque

def shortest_path_to_camp(total_landmarks, connections, current_landmark, camp_landmark):
    visited = [False] * (total_landmarks + 1)
    queue = deque()
    queue.append((current_landmark, 1))
    visited[current_landmark] = True
    while queue:
        landmark, count = queue.popleft()
        if landmark == camp_landmark:
            return count
        for neighbor in connections.get(landmark, []):
            if not visited[neighbor]:
                visited[neighbor] = True
                queue.append((neighbor, count + 1))
    return -1

# Sample input
# total_landmarks = 18
# connections = {1:[2,11,3,4],3:[2,5],4:[2,6],5:[3,9],6:[1,4,7],7:[6,8],8:[7,9],9:[5,8],10:[1,8]}
# current_landmark = 3
# camp_landmark = 9
# print(shortest_path_to_camp(total_landmarks, connections, current_landmark, camp_landmark))
```

## Source / Occurrence Metadata
- Source: `PDSA OPPE1/iitm-pdsa-main/OPE/LostInThejungle.py`
- Occurrences currently confirmed: 1; final count subject to remaining OPPE2/OPPE3 scan.
