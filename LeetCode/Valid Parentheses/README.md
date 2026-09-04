# Valid Parentheses

![Difficulty: Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)
[![LeetCode](https://img.shields.io/badge/LeetCode-Valid_Parentheses-FFA116?style=flat&logo=leetcode)](https://leetcode.com/problems/valid-parentheses/description/)

## Problem / Task Description

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:
1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

### Constraints
- $1 \le s.length \le 10^4$
- `s` consists of parentheses only: `'()[]{}'`.

---

## Approach & Intuition

The problem requires us to verify if open brackets are closed in the correct order. This **Last-In, First-Out (LIFO)** property makes a **Stack** data structure the ideal choice.

### Key Strategy
1. **Traverse the String**: Process the input string character by character.
2. **Push Opening Brackets**: Whenever an opening bracket (`'('`, `'['`, `'{'`) is encountered, push it onto the stack.
3. **Validate Closing Brackets**:
   - If a closing bracket (`')'`, `']'`, `'}'`) is encountered:
     - First, check if the stack is empty. If it is, there is no corresponding opening bracket, making the string invalid immediately.
     - Pop the top character from the stack and verify if it matches the expected opening pair for the current closing bracket.
     - If the pair does not match, return `false`.
4. **Final Check**: After processing all characters, if the stack is empty, all opening brackets were properly closed and matched. If the stack still contains elements, some opening brackets were left unclosed, making the string invalid.

---

## Complexity Analysis

- **Time Complexity:** $\mathcal{O}(N)$
  - We traverse the string of length $N$ exactly once.
  - Push and pop operations on the stack run in constant time, $\mathcal{O}(1)$.

- **Space Complexity:** $\mathcal{O}(N)$
  - In the worst-case scenario (e.g., an input string consisting entirely of opening brackets like `"((((("`), the stack will hold up to $N$ characters.

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