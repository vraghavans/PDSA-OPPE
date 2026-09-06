# Q022 — Journey through Indian Railways

## Student Question

Journey through Indian Railways

India, with its vast and diverse landscape, is connected by an extensive railway network that spans cities, towns, and villages. Trains are an integral part of Indian life, providing an affordable and efficient mode of transportation.

You are tasked with writing a program to help travelers to find the shortest time it takes to travel from one city to another using the Indian Railways.

The railway network is represented using an adjacency list where each city is a node, and the connections between cities are represented as directed edges with travel times.

Write a function min_time_to_travel(num_cities, railways_route, start_city, end_city) that takes the following parameters:

num_cities: An integer n, the total number of cities in the railway network (labeled from 1 to n).

railways_route: A dictionary where keys represent the source cities and the values are lists of tuples (destination city, travel_time) representing the destination city and travel times from source city to destination city.

start_city: An integer, the starting city.

end_city: An integer, the destination city.

The function should return an integer, the minimum time it takes to travel from the starting city to the destination city using the Indian Railways. If there's no way to reach the destination city trom the starting city, return -1.

**Sample Input 1**
```text
4
{1: [(2, 3), (3, 5)],2: [(3, 2), (4, 6)],3: [(4, 1)],4: []}
1
4
```
**Output** `6`

**Sample Input 2**
```text
7
{1: [(2, 3), (3, 5)],2: [(3, 2), (4, 6)],3: [(4, 1)],4: [],5: [(6,5),(7,10), (4,12)],6: [(5,5)],7: [(5,15)]}
6
2
```
**Output** `-1`

### Student Function
```python
def min_time_to_travel(num_cities, railways_route, start_city, end_city):
```

## Full Reference Code
```python
import heapq

def min_time_to_travel(num_cities, railways_route, start_city, end_city):
    min_times = {city: float('inf') for city in range(1, num_cities + 1)}
    min_times[start_city] = 0
    priority_queue = [(0, start_city)]
    while priority_queue:
        current_time, current_city = heapq.heappop(priority_queue)
        if current_city == end_city:
            return current_time
        for neighbor, travel_time in railways_route.get(current_city, []):
            new_time = current_time + travel_time
            if new_time < min_times[neighbor]:
                min_times[neighbor] = new_time
                heapq.heappush(priority_queue, (new_time, neighbor))
    return -1
```

## Source / Occurrence Metadata
- Source: `PDSA OPPE1/iitm-pdsa-main/OPE/min_time_to_travel.py`
- Occurrences currently confirmed: 1; final count subject to remaining OPPE2/OPPE3 scan.
