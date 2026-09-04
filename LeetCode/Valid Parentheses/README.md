# Valid Parentheses

![Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)
![LeetCode](https://img.shields.io/badge/Platform-LeetCode-orange)
![Language](https://img.shields.io/badge/Language-Java-blue)

[Problem Link](https://leetcode.com/problems/valid-parentheses/description/)

## Problem / Task Description

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:
1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

### Constraints
* $1 \le \text{s.length} \le 10^4$
* `s` consists of parentheses only `'()[]{}'`.

---

## Approach & Intuition

The problem requires validating bracket sequences in a **Last-In, First-Out (LIFO)** order. The most recently encountered opening bracket must be the first one to be closed by a matching closing bracket. This LIFO property makes a **Stack** the ideal data structure for this task.

### Algorithm Strategy:
1. **Initialize Stack**: Create a stack to keep track of expected opening brackets.
2. **Iterate Characters**: Traverse each character `ch` in string `s`:
   - **Opening Brackets (`(`, `[`, `{`)**: Push `ch` onto the stack.
   - **Closing Brackets (`)`, `]`, `}`)**:
     - Check if the stack is empty. If it is, return `false` because there is no matching opening bracket.
     - Pop the top character from the stack and verify if it matches the corresponding opening bracket for `ch`. If it doesn't match, return `false`.
3. **Final Check**: After processing the entire string, check if the stack is empty.
   - If the stack is empty, all opening brackets were properly closed $\rightarrow$ Return `true`.
   - If the stack is not empty, some opening brackets remain unclosed $\rightarrow$ Return `false`.

---

## Complexity Analysis

- **Time Complexity:** $\mathcal{O}(n)$
  - We traverse the input string of length $n$ exactly once.
  - Push and pop operations on the stack take $\mathcal{O}(1)$ constant time.

- **Space Complexity:** $\mathcal{O}(n)$
  - In the worst-case scenario (e.g., input string containing only opening brackets like `"((((("`), the stack will store up to $n$ characters.

---

## Solution Code

```java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();

        for (char ch : s.toCharArray()) {

            // Opening brackets
            if (ch == '(' || ch == '[' || ch == '{') {
                stack.push(ch);
            }

            // Closing brackets
            else {
                if (stack.isEmpty()) {
                    return false;
                }

                char top = stack.pop();

                if (ch == ')' && top != '(' ||
                    ch == ']' && top != '[' ||
                    ch == '}' && top != '{') {
                    return false;
                }
            }
        }

        return stack.isEmpty();
    }
}
```