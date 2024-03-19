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

**Solution:**
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
***
#### Problem 3: [Reverse String](https://leetcode.com/problems/reverse-string/)

**Description:**

Write a function that reverses a string. The input string is given as an array of characters s.
You must do this by modifying the input array in-place with O(1) extra memory.


**Example 1:**
```plaintext
Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
```

**Example 2:**
```plaintext
Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
class Solution {

    public void reverseString(char[] s) {
        int head = 0, tail = s.length - 1;
        while (head < tail) {
            char temp = s[head];
            s[head] = s[tail];
            s[tail] = temp;

            tail--;
            head++;
        }
    }
}
```
***
#### Problem 4: [Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)

**Description:**

You are given two integer arrays `nums1` and `nums2`, sorted in non-decreasing order, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.

Merge `nums1` and `nums2` into a single array sorted in non-decreasing order.

The final sorted array should not be returned by the function, but instead be stored inside the array `nums1`. To accommodate this, `nums1` has a length of `m + n`, where the first `m` elements denote the elements that should be merged, and the last `n` elements are set to `0` and should be ignored. `nums2` has a length of `n`.


**Example 1:**
```plaintext
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]

Explanation: The arrays we are merging are [1,2,3] and [2,5,6].
The result of the merge is [1,2,2,3,5,6] with the underlined elements coming from nums1.
```

**Example 2:**
```plaintext
Input: nums1 = [1], m = 1, nums2 = [], n = 0
Output: [1]

Explanation: The arrays we are merging are [1] and [].
The result of the merge is [1].
```

**Example 3:**
```plaintext
Input: nums1 = [0], m = 0, nums2 = [1], n = 1
Output: [1]

Explanation: The arrays we are merging are [] and [1].
The result of the merge is [1].
Note that because m = 0, there are no elements in nums1. The 0 is only there to ensure the merge result can fit in nums1.
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
public class Solution {

    public void merge(int[] nums1, int m, int[] nums2, int n) {
        for (int i = nums1.length - 1; i >= 0; i--) {
            if (m > 0 && n > 0) {
                if (nums1[m - 1] > nums2[n - 1]) {
                    nums1[i] = nums1[m-- - 1];

                } else {
                    nums1[i] = nums2[n-- - 1];
                }
            } else if (m > 0) {
                nums1[i] = nums1[m-- - 1];
            } else if (n > 0) {
                nums1[i] = nums2[n-- - 1];
            }
        }
    }
}
```
***
#### Problem 5: [Find First Palindromic String in The Array](https://leetcode.com/problems/find-first-palindromic-string-in-the-array/)

**Description:**
Given an array of strings `words`, return the first *palindromic* string in the array. 
If there is no such string, return an empty string `""`.
A string is *palindromic* if it reads the same forward and backward.


**Example 1:**
```plaintext
Input: words = ["abc","car","ada","racecar","cool"]
Output: "ada"

Explanation: The first string that is palindromic is "ada".
Note that "racecar" is also palindromic, but it is not the first.
```

**Example 2:**
```plaintext
Input: words = ["notapalindrome","racecar"]
Output: "racecar"

Explanation: The first and only string that is palindromic is "racecar".
```

**Example 3:**
```plaintext
Input: words = ["def","ghi"]
Output: ""

Explanation: There are no palindromic strings, so the empty string is returned.
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
public class Solution {
    public boolean isPalindrome(String s) {
        for (int i = 0; i < s.length() / 2 + 1; i++) {
            if (s.charAt(i) != s.charAt(s.length() - i - 1)) {
                return false;
            }
        }
        return true;
    }

    public String firstPalindrome(String[] words) {
        for (String word : words) {
            if (isPalindrome(word)) {
                return word;
            }
        }
        return "";
    }
}
```
***
#### Problem 6: [Palindrome Number](https://leetcode.com/problems/palindrome-number/)

**Description:**
Given an integer `x`, return `true` if `x` is a palindrome, and `false` otherwise.


**Example 1:**
```plaintext
Input: x = 121
Output: true

Explanation: 121 reads as 121 from left to right and from right to left.
```

**Example 2:**
```plaintext
Input: x = -121
Output: false

Explanation: From left to right, it reads -121. From right to left, it becomes 121-. Therefore it is not a palindrome.
```

**Example 3:**
```plaintext
Input: x = 10
Output: false

Explanation: Reads 01 from right to left. Therefore it is not a palindrome.
```

**Solution 1:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */

public class Solution {

    public boolean isPalindrome(int number) {

        if (number < 0) {
            return false;
        }

        String strNum = number + "";
        for (int i = 0; i < strNum.length() / 2 + 1; i++) {
            if (strNum.charAt(i) != strNum.charAt(strNum.length() - i - 1)) {
                return false;
            }
        }
        return true;
    }
}
```

**Solution 2 (Using `Math` Topic Instead) : [Click Here](https://github.com/Mo-Abdalkader/Problem_Solving/blob/main/Math.md#problem-1-palindrome-number)**
***

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

**Solution:**
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

**Solution:**
```java

```
***
#### Problem 3: [Rearrange Array Elements by Sign](https://leetcode.com/problems/rearrange-array-elements-by-sign/)

**Description:**

You are given a *0-indexed* integer array `nums` of even length consisting of an *equal* number of positive and negative integers.

You should return the array of nums such that the the array follows the given conditions:
1- Every consecutive pair of integers have opposite signs.
2- For all integers with the same sign, the order in which they were present in nums is preserved.
3- The rearranged array begins with a positive integer.

Return the modified array after rearranging the elements to satisfy the aforementioned conditions.

**Example 1:**
```plaintext
Input: nums = [3,1,-2,-5,2,-4]
Output: [3,-2,1,-5,2,-4]

Explanation:
The positive integers in nums are [3,1,2]. The negative integers are [-2,-5,-4].
The only possible way to rearrange them such that they satisfy all conditions is [3,-2,1,-5,2,-4].
Other ways such as [1,-2,2,-5,3,-4], [3,1,2,-2,-5,-4], [-2,3,-5,1,-4,2] are incorrect because they do not satisfy one or more conditions.  
```

**Example 2:**
```plaintext
Input: nums = [-1,1]
Output: [1,-1]

Explanation:
1 is the only positive integer and -1 the only negative integer in nums.
So nums is rearranged to [1,-1].
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
public class Solution {

    public int[] rearrangeArray(int[] nums) {
        int rearrangedArray[] = new int[nums.length];
        int positive = 0, negative = 1;

        for (int i = 0; i < rearrangedArray.length; i++) {
            if (nums[i] > 0) {
                rearrangedArray[positive] = nums[i];
                positive += 2;
            } else {
                rearrangedArray[negative] = nums[i];
                negative += 2;
            }
        }
        return rearrangedArray;
    }
}
```
***

