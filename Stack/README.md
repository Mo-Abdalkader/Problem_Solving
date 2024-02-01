# Stack

- This folder contains solutions to various programming problems related to Stack. 
- The problems are organized based on the [NeetCode](https://neetcode.io/) roadmap
- Starting with [LeetCode](https://leetcode.com/) problems, followed by challenges from other websites.

## Folder Structure
- [Easy](#easy)
- [Medium](#medium)
- [Hard](#hard)

## Problem Solving Approach

1. **LeetCode Problems:**
   - Begin with "Easy" problems and progress to "Medium" and "Hard" based on your comfort and confidence.
   - Follow the [NeetCode](https://neetcode.io/) roadmap for a structured learning path.

2. **Challenges from Other Websites:**
   - Explore problems from different websites to diversify your problem-solving skills.
   - Tackle problems based on their relevance to specific concepts related to Stack.

***
## Problems and Solutions

### Easy

#### Problem 1: [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/)

**Description:**

Given a string s containing just the characters `(`, `)`, `{`, `}`, `[` and `]`, determine if the input string is valid.

An input string is valid if:

- Open brackets must be closed by the same type of brackets.
- Open brackets must be closed in the correct order.
- Every close bracket has a corresponding open bracket of the same type.

**Example 1:**
```plaintext
Input: s = "()"
Output: true
```

**Example 2:**
```plaintext
Input: s = "()[]{}"
Output: true
```

**Example 3:**
```plaintext
Input: s = "(]"
Output: false
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
import java.util.Stack;

public class Solution {

    Stack<Character> stack = new Stack();

    public boolean isValid(String s) {
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '(' || s.charAt(i) == '[' || s.charAt(i) == '{') {
                stack.push(s.charAt(i));
            } else if (stack.isEmpty()) {
                return false;
            } else {
                switch (s.charAt(i)) {
                    case ')':
                        if (stack.pop() != '(') {
                            return false;
                        }
                        break;
                    case ']':
                        if (stack.pop() != '[') {
                            return false;
                        }
                        break;
                    case '}':
                        if (stack.pop() != '{') {
                            return false;
                        }
                        break;
                    default:
                        break;
                }
            }
        }
        return stack.isEmpty();
    }
}
```
***

### Medium
