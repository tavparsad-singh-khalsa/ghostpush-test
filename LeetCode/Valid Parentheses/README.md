# Valid Parentheses

![Difficulty: Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)
![Language: Java](https://img.shields.io/badge/Language-Java-orange)
![Platform: LeetCode](https://img.shields.io/badge/Platform-LeetCode-blue)

[LeetCode Problem Link](https://leetcode.com/problems/valid-parentheses/)

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

### Key Concept: Stack (LIFO - Last In, First Out)
The problem requires that brackets close in the reverse order of their opening. The most recently opened bracket must be the first one to be closed. This Last-In, First-Out pattern makes a **Stack** the perfect data structure to track unmatched opening brackets.

### Step-by-Step Strategy
1. **Initialize Stack**: Create a stack to keep track of expected matching brackets.
2. **Iterate Through Characters**: Process the string character by character.
   - **Opening Bracket (`(`, `[`, `{`)**: Push the character onto the stack.
   - **Closing Bracket (`)`, `]`, `}`)**:
     - If the stack is empty, it means there is a closing bracket without a corresponding opening bracket. Return `false`.
     - Pop the top character from the stack and check if it matches the current closing bracket.
     - If the brackets do not form a valid pair (e.g., `(` matched with `]`), return `false`.
3. **Final Validation**: After processing the entire string, check if the stack is empty:
   - If empty: All opening brackets were properly closed. Return `true`.
   - If not empty: There are unclosed opening brackets remaining. Return `false`.

---

## Complexity Analysis

- **Time Complexity:** $\mathcal{O}(N)$
  - We iterate through the string of length $N$ exactly once.
  - Stack push and pop operations run in $\mathcal{O}(1)$ constant time.

- **Space Complexity:** $\mathcal{O}(N)$
  - In the worst-case scenario (e.g., a string consisting entirely of opening brackets like `"((((("`), the stack will store up to $N$ characters.

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