# Two Sum ![Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)

## Problem / Task Description

Given an array of integers `nums` and an integer `target`, return the *indices of the two numbers* such that they add up to `target`.

You may assume that each input would have **exactly one solution**, and you may not use the same element twice. You can return the answer in any order.

### Constraints:
- $2 \le \text{nums.length} \le 10^4$
- $-10^9 \le \text{nums}[i] \le 10^9$
- $-10^9 \le \text{target} \le 10^9$
- **Only one valid answer exists.**

---

## Approach & Intuition

### Intuition
A naive approach would check all pairs of numbers to see if their sum equals the target, which requires nested loops resulting in an $\mathcal{O}(n^2)$ time complexity. 

To optimize this, we can utilize a **Hash Map (Dictionary)**. While iterating through the array, for any given number $x$, we know its required partner (complement) is $y = \text{target} - x$. If we store every visited number and its index in a hash map, we can check in $\mathcal{O}(1)$ time whether the complement $y$ has already been encountered.

### Algorithm Strategy (One-Pass Hash Table)
1. Initialize an empty hash map `seen` to store the numbers as keys and their corresponding indices as values.
2. Iterate through the `nums` array using both index `i` and value `num`:
   - Calculate the required complement: `complement = target - num`.
   - Check if `complement` exists in `seen`:
     - If **yes**, return `[seen[complement], i]`.
     - If **no**, store the current number and index in the map: `seen[num] = i`.
3. Since the problem guarantees exactly one solution, the function will always exit from inside the loop.

---

## Complexity Analysis

- **Time Complexity:** $\mathcal{O}(n)$
  - We traverse the list containing $n$ elements only once.
  - Each lookup and insertion in the hash table takes $\mathcal{O}(1)$ average time.

- **Space Complexity:** $\mathcal{O}(n)$
  - The extra space required depends on the number of items stored in the hash table, which stores at most $n$ elements in the worst-case scenario.

---

## Solution Code

```python
class Solution:
    def twoSum(self, nums: list[int], target: int) -> list[int]:
        seen = {}
        for i, num in enumerate(nums):
            complement = target - num
            if complement in seen:
                return [seen[complement], i]
            seen[num] = i
        return []
```