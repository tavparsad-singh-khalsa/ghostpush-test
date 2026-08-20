# 1. Two Sum ![Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)

[![LeetCode](https://img.shields.io/badge/LeetCode-Problem_Link-blue?logo=leetcode)](https://leetcode.com/problems/two-sum/description/)
![Tags](https://img.shields.io/badge/Tags-Array%20%7C%20Hash%20Table-blue)

## Problem / Task Description

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have **exactly one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

### Constraints:
- $2 \le \text{nums.length} \le 10^4$
- $-10^9 \le \text{nums[i]} \le 10^9$
- $-10^9 \le \text{target} \le 10^9$
- **Only one valid answer exists.**

---

## Approach & Intuition

### Brute Force Search
1. **Intuition**: The simplest approach is to test every possible pair of numbers in the array to see if their sum matches the given `target`.
2. **Algorithm**:
   - Use two nested loops to check all distinct pairs $(i, j)$ where $j > i$.
   - The outer loop selects the first element `nums[i]`.
   - The inner loop checks every subsequent element `nums[j]`.
   - If `nums[i] + nums[j] == target`, the condition is met, and we return `[i, j]`.

> **Note on Optimization**: While the brute force approach requires no extra memory, it can be optimized from $\mathcal{O}(N^2)$ to $\mathcal{O}(N)$ time complexity by using a **Hash Table** to store each number's index as we iterate, allowing $\mathcal{O}(1)$ average lookups for the complement (`target - current_val`).

---

## Complexity Analysis

- **Time Complexity**: $\mathcal{O}(N^2)$
  - In the worst case, we compare every pair of elements. For an array of size $N$, the total number of comparisons is $\frac{N(N - 1)}{2}$.
- **Space Complexity**: $\mathcal{O}(1)$
  - The algorithm operates in-place without using extra dynamic memory or data structures.

---

## Solution Code

```python
class Solution:
    def twoSum(self, nums: list[int], target: int) -> list[int]:
        """
        Finds indices of the two numbers such that they add up to target.

        :param nums: List[int] - Array of integers
        :param target: int - Target sum
        :return: List[int] - Indices of the two numbers
        """
        n = len(nums)
        for i in range(n):
            for j in range(i + 1, n):
                if nums[i] + nums[j] == target:
                    return [i, j]
        return []
```