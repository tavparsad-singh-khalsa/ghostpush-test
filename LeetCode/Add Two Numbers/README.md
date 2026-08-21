# Add Two Numbers

![Difficulty: Easy](https://img.shields.io/badge/Difficulty-Easy-brightgreen)
![Tag: Algorithm](https://img.shields.io/badge/Tag-Algorithm-blue)
![Language: Java](https://img.shields.io/badge/Language-Java-orange)

[Problem Link on LeetCode](https://leetcode.com/problems/add-two-numbers/)

## Problem / Task Description

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number `0` itself.

### Key Constraints:
- The number of nodes in each linked list is in the range `[1, 100]`.
- `0 <= Node.val <= 9`
- It is guaranteed that the list represents a number that does not have leading zeros.

---

## Approach & Intuition

The problem models column-by-column addition learned in elementary math. Since digits are stored in reverse order, the head of each linked list corresponds to the least significant digit (ones place).

### Strategy:
1. **Dummy Node**: Initialize a `dummy` node to simplify handling edge cases (e.g., setting up the head of the output list).
2. **Pointer & Carry**: Maintain a `current` pointer to build the resulting list and an integer `carry` variable (initialized to `0`) to handle values $\ge 10$.
3. **Traversal Loop**: Loop while there are remaining nodes in `l1` or `l2`, or if a non-zero `carry` remains:
   - Add the values of `l1.val` (if present) and `l2.val` (if present) along with `carry`.
   - Update `carry` for the next position: `carry = sum / 10`.
   - Create a new node with value `sum % 10` and append it to `current.next`.
   - Advance `current` and pointers for `l1` and `l2` if available.
4. **Result**: Return `dummy.next` as the head of the new linked list.

---

## Complexity Analysis

- **Time Complexity:** $\mathcal{O}(\max(N, M))$
  - Where $N$ and $M$ represent the lengths of linked lists `l1` and `l2`, respectively. The loop iterates at most $\max(N, M) + 1$ times.

- **Space Complexity:** $\mathcal{O}(\max(N, M))$
  - The length of the new list is at most $\max(N, M) + 1$. Aside from the nodes created for the output, auxiliary space usage is $\mathcal{O}(1)$.

---

## Solution Code

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(0);
        ListNode current = dummy;
        int carry = 0;

        while (l1 != null || l2 != null || carry != 0) {
            int sum = carry;

            if (l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }

            if (l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }

            carry = sum / 10;
            current.next = new ListNode(sum % 10);
            current = current.next;
        }

        return dummy.next;
    }
}
```