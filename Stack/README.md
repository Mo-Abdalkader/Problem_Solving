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

#### Problem 1: [Min Stack]https://leetcode.com/problems/min-stack/)

**Description:**

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

Implement the MinStack class:

- MinStack() initializes the stack object.
- void push(int val) pushes the element val onto the stack.
- void pop() removes the element on the top of the stack.
- int top() gets the top element of the stack.
- int getMin() retrieves the minimum element in the stack.
You must implement a solution with `O(1)` time complexity `for each function`.

**Example 1:**
```plaintext
Input
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

Output
[null,null,null,null,-3,null,0,-2]

Explanation
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin(); // return -3
minStack.pop();
minStack.top();    // return 0
minStack.getMin(); // return -2
```


**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
import java.util.Objects;
import java.util.Stack;

public class MinStack {

    Stack<Integer> main_stack;
    Stack<Integer> min_stack;

    public MinStack() {
        main_stack = new Stack<>();
        min_stack = new Stack<>();
    }

    public void push(int val) {
        main_stack.push(val);
        if (min_stack.isEmpty() || val <= min_stack.peek()) {
            min_stack.push(val);
        }
    }

    public void pop() {
        if (Objects.equals(main_stack.pop(), min_stack.peek())) {
            min_stack.pop();
        }
    }

    public int top() {
        return main_stack.peek();
    }

    public int getMin() {
        return min_stack.peek();
    }
}

/**
 * Your MinStack object will be instantiated and called as such: MinStack obj =
 * new MinStack(); obj.push(val); obj.pop(); int param_3 = obj.top(); int
 * param_4 = obj.getMin();
 */
```
***
