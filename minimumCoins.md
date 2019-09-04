# Minimum Coins Problem
Given a set of diferent coins, how would you take the fewest amounts of coints to reach a certain value.

## Not Solution but just giving back combinations to achieve value
```
coins=[1,5,10,11,25]

def fewCoin(value, coinset):
  memory = {0:([[]])}
  for val in range(1, value+1):
    memory[val] = []
    for coin in coinset:
      sub = val-coin
      if sub >=0:
        for entries in memory[sub]:
          memory[val].append([*entries, coin])

  return memory[value]

print(fewCoin(27,coins))
```

## Solution giving back both number of coins and what is the specific combination
```
coins=[1,5,10,11,25]

def fewCoin(value, coinset):
  memory = {0:(0,[])}
  # memory = {}
  # memory[0] = (0, [])
  for val in range(1, value+1):
    memory[val] = (float('inf'), [])
    for coin in coinset:
      sub = val-coin
      if sub >=0 and memory[sub][0]+1 <memory[val][0]:
        memory[val] = (memory[sub][0]+1, [*memory[sub][1], coin])
  return memory[val]
print(fewCoin(15,coins))
```
## Zheng's Solution w/ memoization
```
memo = dict()
coinlist = [25, 10, 1]
def min_coins(cents):
    if cents < 1:
        return 0
    if cents not in memo.keys():    
        memo[cents] = min([(cents//x) + min_coins(cents%x) if (cents > x) else cents for x in coinlist])
    return memo[cents]
 ```
 
 ## Zheng's solution w/o memoization
 ```
 coinlist = [25, 10, 1]
def min_coins(cents):
    if cents < 1:
        return 0
    return min([(cents//x) + min_coins(cents%x) if (cents > x) else cents for x in coinlist])
```
