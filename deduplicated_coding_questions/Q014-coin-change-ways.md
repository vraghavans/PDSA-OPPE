# Q014 — Coin Change Ways

## Student Question

Coin Change Ways

You are given a set of coins, each with a different positive denomination, and a target amount of money. Your task is to determine the number of distinct ways you can make up the target amount using the given coins. You have an infinite supply of each coin denomination.

Implement a function coin_change_ways(coins, amount) that takes in a list of coin denominations "coins" and an integer "amount", and returns the number of distinct ways to make up the amount using the given coins.

**Sample input 1**
```text
[1, 2, 5]
5
```
**Output:** `4`

**Sample Input 2**
```text
[2, 3, 4, 7]
7
```
**Output:** `3`

### Student Function
```python
def coin_change_ways(coins, amount):
```

## Full Reference Code
```python
def coin_change_ways(coins, amount):
    dp = [0] * (amount + 1)
    dp[0] = 1
    for coin in coins:
        for i in range(coin, amount + 1):
            dp[i] += dp[i - coin]
    return dp[amount]
```

## Source / Occurrence Metadata
- Source: `PDSA OPPE1/iitm-pdsa-main/OPE/coinChangeWays.py`
- Occurrences currently confirmed: 1; final count subject to remaining OPPE2/OPPE3 scan.
