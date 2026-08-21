# Palindrome Number

![Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)
![Language](https://img.shields.io/badge/Language-Java-orange)
![Tags](https://img.shields.io/badge/Tags-Math-blue)

[Problem Link on LeetCode](https://leetcode.com/problems/palindrome-number/description/)

## Problem / Task Description

Given an integer `x`, return `true` if `x` is a **palindrome**, and `false` otherwise.

An integer is a palindrome when it reads the same forward and backward. For example, `121` is a palindrome while `123` is not.

### Constraints
* $-2^{31} \le x \le 2^{31} - 1$

---

## Approach & Intuition

1. **Handle Edge Cases**: 
   - Any negative number cannot be a palindrome because the negative sign `-` remains at the front (e.g., `-121` reversed becomes `121-`). Therefore, if `x < 0`, we immediately return `false`.

2. **Reverse the Integer**:
   - Store the original value of `x` in a variable `original` to preserve it for comparison later.
   - Maintain a variable `reverse` initialized to `0`.
   - Extract the last digit of `x` using the modulo operator (`x % 10`).
   - Append the digit to `reverse` by shifting `reverse` left by one decimal place (`reverse = reverse * 10 + digit`).
   - Drop the last digit from `x` using integer division (`x / 10`).
   - Repeat this process until `x` becomes `0`.

3. **Comparison**:
   - Once `x` is completely processed, compare `original` with `reverse`. If they are equal, the integer is a palindrome.

---

## Complexity Analysis

- **Time Complexity:** $\mathcal{O}(\log_{10}(x))$ — In each iteration, we divide `x` by `10`, meaning the loop runs once for every digit in `x`. For an integer with $N$ digits, the number of iterations is $\log_{10}(x)$.
- **Space Complexity:** $\mathcal{O}(1)$ — Only a few auxiliary primitive variables (`original`, `reverse`, `digit`) are used, requiring constant extra memory.

---

## Solution Code

```java
class Solution {
    public boolean isPalindrome(int x) {

        // Negative numbers are not palindrome
        if (x < 0) {
            return false;
        }

        int original = x;
        int reverse = 0;

        while (x != 0) {
            int digit = x % 10;
            reverse = reverse * 10 + digit;
            x = x / 10;
        }

        return original == reverse;
    }
}
```