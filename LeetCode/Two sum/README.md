# Two Sum

![Difficulty: Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)
![LeetCode](https://img.shields.io/badge/Platform-LeetCode-orange)
![Language: Java](https://img.shields.io/badge/Language-Java-blue)

## Problem / Task Description

Given an array of integers `nums` and an integer `target`, return the *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have **exactly one solution**, and you may not use the same element twice. You can return the answer in any order.

* **Original Problem Link:** [LeetCode - Two Sum](https://leetcode.com/problems/two-sum/description/)

### Constraints
* $2 \le \text{nums.length} \le 10^4$
* $-10^9 \le \text{nums[i]} \le 10^9$
* $-10^9 \le \text{target} \le 10^9$
* **Only one valid answer exists.**

---

## Approach & Intuition

### Brute Force Approach
The problem asks us to find two distinct indices $i$ and $j$ such that `nums[i] + nums[j] == target`. 

1. **Outer Loop (`i`):** Iterate through each element in the array from index `0` to `nums.length - 1`.
2. **Inner Loop (`j`):** Iterate through every subsequent element from index `i + 1` to `nums.length - 1` to ensure we do not reuse the same element and avoid duplicate pair checks.
3. **Check Condition:** If `nums[i] + nums[j] == target`, immediately return the array containing indices `[i, j]`.
4. **Fallback:** If no such pair is found after checking all combinations, return an empty array `new int[]{}`.

> **Note:** While an optimal solution using a **Hash Table** can achieve $O(N)$ time complexity, this brute-force nested loop approach guarantees finding the correct indices with $O(1)$ auxiliary space complexity.

---

## Complexity Analysis

- **Time Complexity:** $\mathcal{O}(N^2)$
  - In the worst case, we compare every possible pair of elements. For an array of size $N$, the total number of comparisons is $\frac{N(N - 1)}{2}$, leading to quadratic time complexity.

- **Space Complexity:** $\mathcal{O}(1)$
  - No additional data structures (like maps or sets) are allocated. The algorithm operates directly on the input array, consuming constant auxiliary space.

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