# Two Sum

[![Difficulty: Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen.svg)](https://leetcode.com/problems/two-sum/)
[![LeetCode](https://img.shields.io/badge/LeetCode-Solutions-orange.svg)](https://leetcode.com/problems/two-sum/)
[![Language: Java](https://img.shields.io/badge/Language-Java-red.svg)](https://docs.oracle.com/en/java/)

## Problem / Task Description

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have **exactly one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

### Example
- **Input:** `nums = [2, 7, 11, 15]`, `target = 9`
- **Output:** `[0, 1]`
- **Explanation:** Because `nums[0] + nums[1] == 9`, we return `[0, 1]`.

### Constraints
- $2 \le \text{nums.length} \le 10^4$
- $-10^9 \le \text{nums}[i] \le 10^9$
- $-10^9 \le \text{target} \le 10^9$
- **Only one valid answer exists.**

---

## Approach & Intuition

### Brute Force Strategy
The implemented solution uses a **Brute Force** approach to find the two elements:

1. **Outer Loop:** Iterate through the array with index `i` from `0` to `nums.length - 1`.
2. **Inner Loop:** For every element at index `i`, iterate through the rest of the array with index `j` from `i + 1` to `nums.length - 1`. This avoids checking the same element twice and eliminates duplicate pair comparisons.
3. **Condition Check:** Check if `nums[i] + nums[j] == target`.
4. **Return Result:** As soon as a matching pair is found, return their indices `[i, j]`.

> **Note:** While this approach guarantees finding the answer using $O(1)$ extra memory, it can be optimized to $O(N)$ time using a **Hash Table** to trade space for speed.

---

## Complexity Analysis

- **Time Complexity:** $\mathcal{O}(N^2)$  
  In the worst-case scenario, we test every pair in the array. For an array of size $N$, the total number of comparisons is $\frac{N(N - 1)}{2}$, resulting in quadratic time complexity.

- **Space Complexity:** $\mathcal{O}(1)$  
  No additional data structures are used. The algorithm operates directly on the input array using a constant amount of extra memory for loop counters.

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