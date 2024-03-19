#### Problem 1: [Palindrome Number](https://leetcode.com/problems/palindrome-number/)

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
        int reversedNumber = 0;
        int number_temp = number;

        if (number < 0) {
            return false;
        }

        while (number_temp != 0) {
            reversedNumber *= 10;
            reversedNumber += number_temp % 10;
            number_temp = (int) (number_temp / 10);
        }

        return reversedNumber == number;
    }
}
```

**Solution 2 (Using `Two Pointers` Topic Instead) : [Click Here]()**

***
