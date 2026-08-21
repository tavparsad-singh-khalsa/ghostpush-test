# Palindrome Number

![Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)

## Problem / Task Description

Given an integer `x`, return `true` if `x` is a **palindrome**, and `false` otherwise.

An integer is a palindrome when it reads the same backward as forward. For example, `121` is a palindrome while `123` is not.

### Key Constraints:
- $-2^{31} \le x \le 2^{31} - 1$

---

## Approach & Intuition

1. **Negative Number Handling**: 
   - Any negative number cannot be a palindrome because the negative sign sits at the front, but when reversed, it would sit at the end (e.g., `-121` becomes `121-`). Therefore, if `x < 0`, we immediately return `False`.

2. **Reversing the Integer Mathematically**:
   - Instead of converting the integer to a string (which uses extra space), we can reverse the integer mathematically using basic arithmetic operations.
   - We maintain a copy of the initial value in a variable `original`.
   - In a loop while `x != 0`:
     - Extract the last digit of `x` using the modulo operator: `digit = x % 10`.
     - Push the extracted digit into our `reverse` variable: `reverse = reverse * 10 + digit`.
     - Remove the last digit from `x` using floor division: `x = x // 10`.

3. **Comparison**:
   - Once `x` becomes `0`, the loop terminates.
   - We return the boolean result of comparing `original == reverse`.

---

## Complexity Analysis

- **Time Complexity:** $\mathcal{O}(\log_{10}(x))$  
  In each iteration, we divide $x$ by $10$. Thus, the total number of iterations is equal to the number of digits in $x$, which is $\lfloor\log_{10}(x)\rfloor + 1$.

- **Space Complexity:** $\mathcal{O}(1)$  
  The algorithm operates in constant space. It uses a fixed number of auxiliary integer variables (`original`, `reverse`, and `digit`) without allocating any dynamic data structures.

---

## Solution Code

```python
class Solution:
    def isPalindrome(self, x: int) -> bool:

        if x < 0:
            return False

        original = x
        reverse = 0

        while x != 0:
            digit = x % 10
            reverse = reverse * 10 + digit
            x = x // 10

        return original == reverse
```