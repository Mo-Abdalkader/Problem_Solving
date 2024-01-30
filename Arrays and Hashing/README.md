# Arrays and Hashing

- This folder contains solutions to various programming problems related to arrays and hashing. 
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
   - Tackle problems based on their relevance to specific concepts related to arrays and hashing.

***
## Problems and Solutions

### Easy

#### Problem 1: [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

**Description:**
Given an integer array `nums`, return true if any value appears at least twice in the array, and return false if every element is distinct.

**Example 1:**
```plaintext
Input: nums = [1,2,3,1]
Output: true
```

**Example 2:**
```plaintext
Input: nums = [1,2,3,4]
Output: false
```

**Example 3:**
```plaintext
Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
import java.util.HashMap;

class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashMap hashMap = new HashMap();
        for (int num : nums) {
            if (hashMap.containsKey(num)) {
                return true;
            } else {
                hashMap.put(num, 1);
            }
        }
        return false;
    }
}
```
***

#### Problem 2: [Valid Anagram](https://leetcode.com/problems/valid-anagram/description/)

**Description:**

Given two strings s and t, return true if t is an anagram of s, and false otherwise.
An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

**Example 1:**
```plaintext
Input: s = "anagram", t = "nagaram"
Output: true
```

**Example 2:**
```plaintext
Input: s = "rat", t = "car"
Output: false
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
import java.util.Arrays;

public class Solution {

    public boolean isAnagram(String s, String t) {
        if (s.length() == t.length()) {
            char[] s_array = s.toCharArray();
            char[] t_array = t.toCharArray();

            Arrays.sort(s_array);
            Arrays.sort(t_array);

            return (new String(s_array).equals(new String(t_array)));
        }
        return false;
    }
}
```
***
***

#### Problem 3: [Two Sum](https://leetcode.com/problems/two-sum/description/)

**Description:**

Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.

**Example 1:**
```plaintext
Input: nums = [2,7,11,15], target = 9
Output: [0,1]

Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**Example 2:**
```plaintext
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**Example 3:**
```plaintext
Input: nums = [3,3], target = 6
Output: [0,1]
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
import java.util.HashMap;

public class Solution {

    HashMap<Integer, Integer> hashMap = new HashMap();

    public int[] twoSum(int[] nums, int target) {
        int[] answer = new int[2];
        for (int i = 0; i < nums.length; i++) {
            int theSecondValue = target - nums[i];
            if (hashMap.containsKey(theSecondValue)) {
                answer[0] = hashMap.get(theSecondValue);
                answer[1] = i;
                break;
            } else {
                hashMap.put(nums[i], i);
            }
        }
        return answer;
    }
}
```
***



10 * 10^2 + 3
