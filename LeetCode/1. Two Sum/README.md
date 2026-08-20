# 1. Two Sum

![Difficulty: Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)
![Language: Java](https://img.shields.io/badge/Language-Java-orange)
![Platform: LeetCode](https://img.shields.io/badge/Platform-LeetCode-blue)

[Problem Link](https://leetcode.com/problems/two-sum/description/)

---

## Problem / Task Description

Given an array of integers `nums` and an integer `target`, return the *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have **exactly one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

### Constraints
* $2 \le \text{nums.length} \le 10^4$
* $-10^9 \le \text{nums[i]} \le 10^9$
* $-10^9 \le \text{target} \le 10^9$
* **Only one valid answer exists.**

---

## Approach & Intuition

The provided solution uses a **Brute Force** approach:

1. **Outer Loop**: Iterate through each element in the array with index `i` from `0` to `nums.length - 1`.
2. **Inner Loop**: Iterate through all subsequent elements with index `j` from `i + 1` to `nums.length - 1`.
3. **Check Sum**: For each pair `(i, j)`, test if `nums[i] + nums[j] == target`.
4. **Return Result**: Once a matching pair is found, immediately return their indices `new int[]{i, j}`.
5. If no pair is found (though guaranteed by constraints to exist), return an empty array.

> **Note**: While an optimal $O(N)$ solution can be achieved using a **Hash Table**, this brute force approach evaluates every unique pair of elements directly without requiring extra memory overhead.

---

## Complexity Analysis

- **Time Complexity:** $\mathcal{O}(N^2)$
  - In the worst case, the algorithm compares every pair of numbers. The inner loop executes $\frac{N(N-1)}{2}$ times, leading to quadratic time complexity relative to the array length $N$.
  
- **Space Complexity:** $\mathcal{O}(1)$
  - No additional data structures are used. Memory consumption remains constant regardless of the input size.

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