# Two Sum

![Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)
![LeetCode](https://img.shields.io/badge/Platform-LeetCode-orange)
![Python](https://img.shields.io/badge/Language-Python-blue)

## Problem / Task Description

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have **exactly one solution**, and you may not use the *same* element twice. You can return the answer in any order.

### Example
- **Input:** `nums = [2, 7, 11, 15]`, `target = 9`
- **Output:** `[0, 1]`
- **Explanation:** Because `nums[0] + nums[1] == 9`, we return `[0, 1]`.

### Constraints
- $2 \le \text{nums.length} \le 10^4$
- $-10^9 \le \text{nums[i]} \le 10^9$
- $-10^9 \le \text{target} \le 10^9$
- **Only one valid answer exists.**

---

## Approach & Intuition

### Hash Map (One-Pass)
1. **Brute Force Discard:** A naive approach uses nested loops to check all pairs, resulting in $O(n^2)$ time complexity. We can do significantly better.
2. **Key Insight:** For any number `x`, we are looking for a complement `y` such that $x + y = \text{target}$, which means $y = \text{target} - x$.
3. **Data Structure:** A Hash Map (dictionary in Python) allows $O(1)$ average-time lookups to check if the complement has already been processed.
4. **Strategy:**
   - Iterate through the array using index `i` and value `num`.
   - Compute `complement = target - num`.
   - If `complement` exists in our dictionary, return its stored index along with the current index `i`.
   - Otherwise, store `num` as the key and `i` as its value in the dictionary.

---

## Complexity Analysis

- **Time Complexity:** $\mathcal{O}(n)$
  - We traverse the list containing $n$ elements only once.
  - Each lookup and insertion in the hash table takes $\mathcal{O}(1)$ average time.

- **Space Complexity:** $\mathcal{O}(n)$
  - The extra space required depends on the number of items stored in the hash map, which stores at most $n$ elements in the worst case.

---

## Solution Code

```python
class Solution:
    def twoSum(self, nums: list[int], target: int) -> list[int]:
        """
        Finds two indices in nums such that their values sum to target.
        
        :param nums: List of integers
        :param target: Target sum
        :return: List containing the two 0-indexed positions
        """
        seen = {}
        
        for i, num in enumerate(nums):
            complement = target - num
            if complement in seen:
                return [seen[complement], i]
            seen[num] = i
            
        return []
```