# Q021 — Minimize Cost to Reach the Destination

## Student Question

Minimize cost to reach the destination

You are given a grid of size m x n with positive integer values representing the cost you have to pay in each cell. You can only jump either one cell down or one cell right at a point in time. Your goal is to find the minimum cost to reach the bottom-right corner cell (m-1, n-1) of the grid, starting from the top-left corner cell (0, 0).

Write a function min_cost(m, n, grid_costs) that takes in two integers m and n representing the number of rows (indexed from 0 to m-1) and the number of columns (indexed from 0 to n-1), and a 2D nested list grid_costs representing the cost of each cell.

The function should return an integer indicating the minimum cost to reach the bottom-right corner cell (m-1, n-1) of the grid starting from the top-left corner cell (0, 9).

**Sample Input 1**
```text
3
3
[[1, 3, 1],[1, 5, 1],[4, 2, 1]]
```
**Output** `7`

**Sample Input 2**
```text
3
3
[[1, 3, 2],[1, 2, 4],[4, 1, 1]]
```
**Output** `6`

### Student Function
```python
def min_cost(m, n, grid_costs):
```

## Full Reference Code
```python
def min_cost(m, n, grid_costs):
    dp = [[0] * n for _ in range(m)]
    dp[0][0] = grid_costs[0][0]
    for j in range(1, n):
        dp[0][j] = dp[0][j-1] + grid_costs[0][j]
    for i in range(1, m):
        dp[i][0] = dp[i-1][0] + grid_costs[i][0]
    for i in range(1, m):
        for j in range(1, n):
            dp[i][j] = grid_costs[i][j] + min(dp[i-1][j], dp[i][j-1])
    return dp[m-1][n-1]
```

## Source / Occurrence Metadata
- Source: `PDSA OPPE1/iitm-pdsa-main/OPE/min_cost.py`
- Occurrences currently confirmed: 1; final count subject to remaining OPPE2/OPPE3 scan.
