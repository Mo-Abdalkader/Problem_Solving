# Two Pointers

- This folder contains solutions to various programming problems related to Two Pointers Technique. 
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
   - Tackle problems based on their relevance to specific concepts related to Two Pointers Ttechnique.

***
## Problems and Solutions

### Easy

#### Problem 1: [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)

**Description:**

A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.


**Example 1:**
```plaintext
Input: s = "A man, a plan, a canal: Panama"
Output: true

Explanation: "amanaplanacanalpanama" is a palindrome.
```

**Example 2:**
```plaintext
Input: s = "race a car"
Output: false

Explanation: "raceacar" is not a palindrome.
```

**Example 3:**
```plaintext
Input: s = " "
Output: true

Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
```

**Solution 1:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
public class Solution {

    public boolean isPalindrome(String s) {
        s = s.toLowerCase();
        String new_string = "";
        int head, tail;

        for (int i = 0; i < s.length(); i++) {
            if ((s.charAt(i) >= 'a' && s.charAt(i) <= 'z') || s.charAt(i) >= '0' && s.charAt(i) <= '9') {
                new_string += s.charAt(i);
            }
        }

        for (head = 0; head < new_string.length(); head++) {
            tail = new_string.length() - head - 1;

            if (new_string.charAt(head) != new_string.charAt(tail)) {
                return false;
            }

            if (head >= tail) {
                break;
            }
        }
        return true;
    }
}
```

**Solution 2 (The Best):**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
public class Solution {

    public boolean isPalindrome(String s) {
        s = s.toLowerCase();
        int head = 0, tail = s.length() - 1;
        boolean head_flag = false, tail_flag = false;

        while (head < tail) {
            if (((s.charAt(head) >= 'a' && s.charAt(head) <= 'z')) || (s.charAt(head) >= '0' && s.charAt(head) <= '9')) {
                head_flag = true;
            } else {
                head++;
                head_flag = false;
            }

            if (((s.charAt(tail) >= 'a' && s.charAt(tail) <= 'z')) || (s.charAt(tail) >= '0' && s.charAt(tail) <= '9')) {
                tail_flag = true;
            } else {
                tail--;
                tail_flag = false;
            }
            if (head_flag && tail_flag) {
                if (s.charAt(head) == s.charAt(tail)) {
                    head++;
                    tail--;
                } else {
                    return false;
                }
            }
        }
        return true;
    }
}
```
***

### Medium
