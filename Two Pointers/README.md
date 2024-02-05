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
#### Problem 2: [Valid Palindrome II](https://leetcode.com/problems/valid-palindrome-ii/)

**Description:**

Given a string s, return true if the s can be palindrome after deleting at most one character from it.


**Example 1:**
```plaintext
Input: s = "aba"
Output: true
```

**Example 2:**
```plaintext
Input: s = "abca"
Output: true

Explanation: You could delete the character 'c'.
```

**Example 3:**
```plaintext
Input: s = "abc"
Output: false
```

**Solution 1:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
public class Solution {

    boolean char_deleted = false;

    public boolean validPalindrome(String s) {
        int head = 0, tail = s.length() - 1;

        if (s.length() <= 2 && !char_deleted) {
            return true;
        }

        for (int i = 0; i < s.length(); i++) {
            if (head >= tail) {
                return true;
            }

            if (s.charAt(head) == s.charAt(tail)) {
                head++;
                tail--;
            } else if (!char_deleted) {
                char_deleted = true;
                if (validPalindrome(s.substring(head + 1, tail + 1)) || validPalindrome(s.substring(head, tail))) {
                    return true;
                }
                break;
            } else {
                break;
            }
        }
        return false;
    }
}
```


### Medium

#### Problem 1: [Two Sum II](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

**Description:**

Given a 1-indexed array of integers numbers that is already sorted in non-decreasing order
Find two numbers such that they add up to a specific target number. 
Let these two numbers be numbers[index1] and numbers[index2] where 1 <= index1 < index2 <= numbers.length.

Return the indices of the two numbers, index1 and index2, added by one as an integer array [index1, index2] of length 2.

- The tests are generated such that there is exactly one solution. You may not use the same element twice.
- Your solution must use only constant extra space.


**Example 1:**
```plaintext
Input: numbers = [2,7,11,15], target = 9
Output: [1,2]

Explanation: The sum of 2 and 7 is 9. Therefore, index1 = 1, index2 = 2. We return [1, 2].
```

**Example 2:**
```plaintext
Input: numbers = [2,3,4], target = 6
Output: [1,3]

Explanation: The sum of 2 and 4 is 6. Therefore index1 = 1, index2 = 3. We return [1, 3].
```

**Example 3:**
```plaintext
Input: numbers = [-1,0], target = -1
Output: [1,2]

Explanation: The sum of -1 and 0 is -1. Therefore index1 = 1, index2 = 2. We return [1, 2].
```

**Solution 1:**
```java
/**
 *
 * @author Mohamed ِAbdalkader
 */

public class Solution {

    public int[] twoSum(int[] numbers, int target) {
        int tail = numbers.length - 1;
        int[] output = new int[2];

        for (int head = 0; head < numbers.length;) {
            if (numbers[head] + numbers[tail] > target) {
                tail--;
            } else if (numbers[head] + numbers[tail] < target) {
                head++;
            }

            if (numbers[head] + numbers[tail] == target) {
                output[0] = head + 1;
                output[1] = tail + 1;
                return output;
            }
        }
        return output;
    }
}
```
***

#### Problem 2: [3 Sum](https://leetcode.com/problems/3sum/)

**Description:**

Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j, i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.


**Example 1:**
```plaintext
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]

Explanation: 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.
```

**Example 2:**
```plaintext
Input: nums = [0,1,1]
Output: []

Explanation: The only possible triplet does not sum up to 0.
```

**Example 3:**
```plaintext
Input: nums = [0,0,0]
Output: [[0,0,0]]

Explanation: The only possible triplet sums up to 0.
```

**Solution 1:**
```java

```
***
