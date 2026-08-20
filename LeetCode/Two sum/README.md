# Two Sum
![Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)
![Language](https://img.shields.io/badge/Language-Java-orange)
![Platform](https://img.shields.io/badge/Platform-LeetCode-blue)

[Problem Link](https://leetcode.com/problems/two-sum/description/)

## Problem / Task Description

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have **exactly one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

### Constraints
* $2 \le \text{nums.length} \le 10^4$
* $-10^9 \le \text{nums}[i] \le 10^9$
* $-10^9 \le \text{target} \le 10^9$
* **Only one valid answer exists.**

---

## Approach & Intuition

The problem asks us to find two distinct indices $i$ and $j$ in the array `nums` such that `nums[i] + nums[j] == target`.

### Brute-Force Strategy (Implemented)
1. **Outer Loop**: Iterate through the array starting from index `i = 0` to `nums.length - 1`.
2. **Inner Loop**: Iterate through all subsequent elements starting from index `j = i + 1` to `nums.length - 1`.
3. **Check Condition**: For every pair `(i, j)`, calculate their sum. If `nums[i] + nums[j] == target`, immediately return `new int[]{i, j}`.
4. **Fallback**: If no such pair is found, return an empty array `new int[]{}`.

> **Optimization Note**: While this brute-force approach works with $O(1)$ auxiliary space, an optimal $O(N)$ time complexity solution can be achieved using a **Hash Table** to store each number's value and its index as we iterate through the array.

---

## Complexity Analysis

- **Time Complexity:** $\mathcal{O}(N^2)$
  - In the worst case, we check all possible pairs in the array. The total number of iterations is $\frac{N(N-1)}{2}$, where $N$ is the length of `nums`.
  
- **Space Complexity:** $\mathcal{O}(1)$
  - No additional data structures are allocated. The algorithm uses a constant amount of extra memory.

---

## Solution Code

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[]{};
    }
}
```