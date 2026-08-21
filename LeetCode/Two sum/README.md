# Two Sum ![Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)

[![LeetCode](https://img.shields.io/badge/LeetCode-Two%20Sum-FFA116?style=flat&logo=leetcode)](https://leetcode.com/problems/two-sum/)
![Array](https://img.shields.io/badge/Topic-Array-blue)
![Hash Table](https://img.shields.io/badge/Topic-Hash%20Table-blue)

## Problem / Task Description

Given an array of integers `nums` and an integer `target`, return **indices of the two numbers** such that they add up to `target`.

You may assume that each input would have **exactly one solution**, and you may not use the *same* element twice. You can return the answer in any order.

### Example 1:
> **Input:** `nums = [2,7,11,15], target = 9`  
> **Output:** `[0,1]`  
> **Explanation:** Because `nums[0] + nums[1] == 9`, we return `[0, 1]`.

### Example 2:
> **Input:** `nums = [3,2,4], target = 6`  
> **Output:** `[1,2]`

### Constraints:
- `2 <= nums.length <= 10^4`
- `-10^9 <= nums[i] <= 10^9`
- `-10^9 <= target <= 10^9`
- **Only one valid answer exists.**

---

## Approach & Intuition

### Brute Force Approach

The simplest strategy to solve this problem is to check every possible pair of numbers in the array to see if their sum equals the `target`.

1. **Outer Loop (`i`)**: Iterates through each element in the array from index `0` to `nums.length - 1`.
2. **Inner Loop (`j`)**: Iterates through all subsequent elements from index `i + 1` to `nums.length - 1`. This ensures we do not compare an element with itself and avoid re-checking pairs.
3. **Condition Check**: In each iteration, we evaluate if `nums[i] + nums[j] == target`.
4. **Return**: Once a matching pair is found, we immediately return an array containing their indices `[i, j]`.

---

## Complexity Analysis

- **Time Complexity:** $\mathcal{O}(n^2)$  
  Where $n$ is the length of the array `nums`. In the worst-case scenario, the nested loops will explore all pairs, resulting in $\frac{n(n - 1)}{2}$ comparisons.

- **Space Complexity:** $\mathcal{O}(1)$  
  The algorithm uses a constant amount of extra space since no auxiliary data structures are used.

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