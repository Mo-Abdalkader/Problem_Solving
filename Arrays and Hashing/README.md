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

#### Problem 2: [Valid Anagram](https://leetcode.com/problems/valid-anagram/)

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

#### Problem 4: [Replace Elements With Greatest Element on Right Side](https://leetcode.com/problems/replace-elements-with-greatest-element-on-right-side/)

**Description:**

Given an array `arr`, replace every element in that array with the greatest element among the elements to its right, and replace the last element with `-1`.

After doing so, return the array.

**Example 1:**
```plaintext
Input: arr = [17,18,5,4,6,1]
Output: [18,6,6,6,1,-1]

Explanation: 
- index 0 --> the greatest element to the right of index 0 is index 1 (18).
- index 1 --> the greatest element to the right of index 1 is index 4 (6).
- index 2 --> the greatest element to the right of index 2 is index 4 (6).
- index 3 --> the greatest element to the right of index 3 is index 4 (6).
- index 4 --> the greatest element to the right of index 4 is index 5 (1).
- index 5 --> there are no elements to the right of index 5, so we put -1.
```

**Example 2:**
```plaintext
Input: arr = [400]
Output: [-1]

Explanation: There are no elements to the right of index 0.
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
public class Solution {

    public int[] replaceElements(int[] arr) {
        int[] output = new int[arr.length];
        int greatest = Integer.MIN_VALUE;
        for (int index = arr.length - 1; index >= 0; index--) {
            if (index != arr.length - 1) {
                output[index] = greatest;
            } else {
                output[index] = -1;
            }
            if (arr[index] > greatest) {
                greatest = arr[index];
            }
        }
        return output;
    }
}
```
***

#### Problem 5: [Roman to Integer](https://leetcode.com/problems/roman-to-integer/)

**Description:**

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
For example, 2 is written as II in Roman numeral, just two ones added together. 12 is written as XII, which is simply X + II. The number 27 is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

I can be placed before V (5) and X (10) to make 4 and 9. 
X can be placed before L (50) and C (100) to make 40 and 90. 
C can be placed before D (500) and M (1000) to make 400 and 900.
Given a roman numeral, convert it to an integer.

**Example 1:**
```plaintext
Input: s = "III"
Output: 3

Explanation: III = 3.
```

**Example 2:**
```plaintext
Input: s = "LVIII"
Output: 58

Explanation: L = 50, V= 5, III = 3.
```

**Example 3:**
```plaintext
Input: s = "MCMXCIV"
Output: 1994

Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
import java.util.HashMap;

public class Solution {

    HashMap<Character, Integer> hashMap;

    private void initHashMap() {
        hashMap = new HashMap();
        hashMap.put('I', 1);
        hashMap.put('V', 5);
        hashMap.put('X', 10);
        hashMap.put('L', 50);
        hashMap.put('C', 100);
        hashMap.put('D', 500);
        hashMap.put('M', 1000);
    }

    public int romanToInt(String s) {
        initHashMap();
        int output = 0;
        int previous_value = hashMap.get(s.charAt(s.length() - 1));;

        for (int i = s.length() - 1; i >= 0; i--) {
            int current_number = hashMap.get(s.charAt(i));
            if (previous_value <= current_number) {
                output += current_number;
            } else {
                output -= current_number;
            }
            previous_value = current_number;
        }
        return output;
    }
}
```
***

#### Problem 6: [First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/)

**Description:**

Given a string `s`, find the `first non-repeating character` in it and return its `index`. If it does not exist, return `-1`.

**Example 1:**
```plaintext
Input: s = "leetcode"
Output: 0
```

**Example 2:**
```plaintext
Input: s = "loveleetcode"
Output: 2
```

**Example 3:**
```plaintext
Input: s = "aabb"
Output: -1
```

**Solution 1:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
import java.util.HashMap;

public class Solution {
    HashMap<Character, Integer> hashMap = new HashMap<>();

    public int firstUniqChar(String s) {
        for (int i = 0; i < s.length(); i++) {
            char key = s.charAt(i);
            int value = 1;

            if (hashMap.containsKey(key)) {
                value = hashMap.get(key);
                value += 1;
            }
            hashMap.put(key, value);
        }

        for (int i = 0; i < s.length(); i++) {
            char key = s.charAt(i);
            if (hashMap.get(key) == 1) {
                return i;
            }
        }
        return -1;
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
    public int firstUniqChar(String s) {
        int[] arr = new int[26];

        for (int i = 0; i < s.length(); i++) {
            int index = s.charAt(i) - 'a';
            arr[index]++;
        }

        for (int i = 0; i < s.length(); i++) {
            int index = s.charAt(i) - 'a';
            if (arr[index] == 1) {
                return i;
            }
        }
        return -1;
    }
}
```
***

#### Problem 7: [First Letter to Appear Twice](https://leetcode.com/problems/first-letter-to-appear-twice/)

**Description:**

Given a string s consisting of lowercase English letters, return the first letter to appear twice.

Note:
- A letter a appears twice before another letter b if the second occurrence of a is before the second occurrence of b.
- s will contain at least one letter that appears twice.

**Example 1:**
```plaintext
Input: s = "abccbaacz"
Output: "c"

Explanation:
The letter 'a' appears on the indexes 0, 5 and 6.
The letter 'b' appears on the indexes 1 and 4.
The letter 'c' appears on the indexes 2, 3 and 7.
The letter 'z' appears on the index 8.
The letter 'c' is the first letter to appear twice, because out of all the letters the index of its second occurrence is the smallest.
```

**Example 2:**
```plaintext
Input: s = "abcdd"
Output: "d"

Explanation:
The only letter that appears twice is 'd' so we return 'd'.
```

**Solution 1:**
```java
/**
 *
 * @author Mohamed ِAbdalkader
 */
import java.util.HashMap;

public class First_letter_to_appear {
    HashMap<Character, Integer> hashMap = new HashMap<>();

    public char repeatedCharacter(String s) {
        for (int i = 0; i < s.length(); i++) {
            if (hashMap.containsKey(s.charAt(i))) {
                return s.charAt(i);
            } else {
                hashMap.put(s.charAt(i), 1);
            }
        }
        return ' '; // Useless
    }
}
```

**Solution 2 (The Best):**
```java
/**
 *
 * @author Mohamed ِAbdalkader
 */
public class Solution {

    public char repeatedCharacter(String s) {
        int[] chars_array = new int[26];

        for (int i = 0; i < s.length(); i++) {
            int index = s.charAt(i) - 'a';
            if (chars_array[index] == 1) {
                return s.charAt(i);
            } else {
                chars_array[index] = 1;
            }
        }
        return ' '; // Useless
    }
}
```
***
#### Problem 8: [Length of Last Word](https://leetcode.com/problems/length-of-last-word/)

**Description:**

Given a string s consisting of words and spaces, return the length of the last word in the string.
A word is a maximal substring consisting of non-space characters only.

**Example 1:**
```plaintext
Input: s = "Hello World"
Output: 5

Explanation: The last word is "World" with length 5.
```

**Example 2:**
```plaintext
Input: s = "   fly me   to   the moon  "
Output: 4

Explanation: The last word is "moon" with length 4.
```

**Example 3:**
```plaintext
Input: s = "luffy is still joyboy"
Output: 6

Explanation: The last word is "joyboy" with length 6.
```

**Solution 1:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
public class Solution {

    public int lengthOfLastWord(String s) {
        int lengthOfLastWord = 0;

        for (int i = s.length() - 1; i >= 0; i--) {
            if (s.charAt(i) == ' ') {
                if (lengthOfLastWord != 0) {
                    return lengthOfLastWord;
                }
            } else {
                lengthOfLastWord++;
            }
        }
        return lengthOfLastWord;
    }
}
```
***

### Medium

#### Problem 1: [Group Anagrams](https://leetcode.com/problems/group-anagrams/)

**Description:**

Given an array of strings strs, group the anagrams together. You can return the answer in any order.
An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

**Example 1:**
```plaintext
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
```

**Example 2:**
```plaintext
Input: strs = [""]
Output: [[""]]
```

**Example 3:**
```plaintext
Input: strs = ["a"]
Output: [["a"]]
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
import java.util.List;
import java.util.ArrayList;
import java.util.HashMap;
import java.util.Arrays;

public class Solution {

    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> parentList = new ArrayList();
        
        HashMap<String, ArrayList<String>> hashMap = new HashMap();
        ArrayList<String> subList;
        
        for (String str : strs) {
            char[] str_chars_array = str.toCharArray();
            Arrays.sort(str_chars_array);
            String rearranged_str_chars = new String(str_chars_array);

            if (hashMap.containsKey(rearranged_str_chars)) {
                subList = hashMap.get(rearranged_str_chars);
            } else {
                subList = new ArrayList<>();
            }
            subList.add(str);
            hashMap.put(rearranged_str_chars, subList);
        }

        for (List<String> list : hashMap.values()) {
            parentList.add(list);
        }

        return parentList;
    }
}
```
***

#### Problem 2: [Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)

**Description:**

Given an integer array nums and an integer k, return the k most frequent elements. You may return the answer in any order.

**Example 1:**
```plaintext
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

**Example 2:**
```plaintext
Input: nums = [1], k = 1
Output: [1]
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */


import java.util.HashMap;
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;

public class Solution {

    public int[] topKFrequent(int[] nums, int k) {
        int[] topKFrequent = new int[k];

        HashMap<Integer, Integer> hashMap = new HashMap();
        for (int i = 0; i < nums.length; i++) {
            if (hashMap.containsKey(nums[i])) {
                hashMap.put(nums[i], hashMap.get(nums[i]) + 1);
            } else {
                hashMap.put(nums[i], 1);
            }
        }

        ArrayList<KFrequent> kFrequentArray = new ArrayList<>();
        for (int key : hashMap.keySet()) {
            KFrequent object = new KFrequent(key, hashMap.get(key));
            kFrequentArray.add(object);
        }

        Collections.sort(kFrequentArray, new comp());

        for (int i = 0; i < topKFrequent.length; i++) {
            topKFrequent[i] = kFrequentArray.get(i).number;
        }
        return topKFrequent;
    }
}

class KFrequent {

    int number;
    int frequent;

    public KFrequent(int number, int frequent) {
        this.number = number;
        this.frequent = frequent;
    }
}

class comp implements Comparator<KFrequent> {

    @Override
    public int compare(KFrequent o1, KFrequent o2) {
        if (o1.frequent < o2.frequent) {
            return 1;
        } else if (o1.frequent > o2.frequent) {
            return -1;
        } else {
            return 0;
        }
    }
}
```
***

#### Problem 3: [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)

**Description:**

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].
The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

**Example 1:**
```plaintext
Input: nums = [1,2,3,4]
Output: [24,12,8,6]
```

**Example 2:**
```plaintext
Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
public class Solution {

    public int[] productExceptSelf(int[] nums) {
        int[] productExceptSelf = new int[nums.length];
        boolean is_contains_zero = false;
        int total_product = 1;

        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                total_product *= nums[i];
            } else {
                if (is_contains_zero) {
                    return productExceptSelf; // zeros
                } else {
                    is_contains_zero = true;
                }
            }
        }

        for (int i = 0; i < nums.length; i++) {
            if (is_contains_zero) {
                if (nums[i] == 0) {
                    productExceptSelf[i] = total_product;
                    return productExceptSelf; // Zeros except zero position
                }
            } else {
                productExceptSelf[i] = total_product / nums[i]; // No zeros
            }
        }
        return productExceptSelf;
    }
}
```
***
#### Problem 4: [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/)

**Description:**

Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

- Each row must contain the digits 1-9 without repetition.
- Each column must contain the digits 1-9 without repetition.
- Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.

**Note:**
- A Sudoku board (partially filled) could be valid but is not necessarily solvable.
- Only the filled cells need to be validated according to the mentioned rules.

**Example 1:**
```plaintext
Input: board = 
[["5","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
Output: true
```

**Example 2:**
```plaintext
Input: board = 
[["8","3",".",".","7",".",".",".","."]
,["6",".",".","1","9","5",".",".","."]
,[".","9","8",".",".",".",".","6","."]
,["8",".",".",".","6",".",".",".","3"]
,["4",".",".","8",".","3",".",".","1"]
,["7",".",".",".","2",".",".",".","6"]
,[".","6",".",".",".",".","2","8","."]
,[".",".",".","4","1","9",".",".","5"]
,[".",".",".",".","8",".",".","7","9"]]
Output: false

Explanation: Same as Example 1, except with the 5 in the top left corner being modified to 8. Since there are two 8's in the top left 3x3 sub-box, it is invalid.
```

**Solution:**
```java
/**
 *
 * @author Mohamed ِAbdalkader
 */
public class Solution {

    int[]   row_array;
    int[][] column_array = new int[9][9];
    int[][] box_array = new int[9][9];

    private static int getBoxIndex(int i, int j) {
        int bowIndex = 2;

        if (i < 3) {
            bowIndex = 0;
        } else if (i < 6) {
            bowIndex = 1;
        }

        return bowIndex * 3 + (int) (j / 3) % 3;
    }

    public boolean isValidSudoku(char[][] board) {

        for (int i = 0; i < board.length; i++) {
            row_array = new int[9];

            for (int j = 0; j < board[i].length; j++) {
                if (board[i][j] >= '1' && board[i][j] <= '9') {
                    int number = (int) board[i][j] - 49; // ASCII for number 1

                    if (row_array[number] != 1) {
                        row_array[number] = 1;
                    } else {
                        return false;
                    }

                    if (column_array[j][number] != 1) {
                        column_array[j][number] = 1;
                    } else {
                        return false;
                    }

                    int box_index = getBoxIndex(i, j);
                    if (box_array[box_index][number] != 0) {
                        return false;
                    } else {
                        box_array[box_index][number] = 1;
                    }
                }
            }
        }
        return true;
    }
}
```
***

#### Problem 5: [Group The People Given The Group Size They Belong To](https://leetcode.com/problems/group-the-people-given-the-group-size-they-belong-to/)

**Description:**

There are n people that are split into some unknown number of groups. Each person is labeled with a unique ID from 0 to n - 1.
You are given an integer array groupSizes, where groupSizes[i] is the size of the group that person i is in. For example, if groupSizes[1] = 3, then person 1 must be in a group of size 3.
Return a list of groups such that each person i is in a group of size groupSizes[i].
Each person should appear in exactly one group, and every person must be in a group. If there are multiple answers, return any of them. It is guaranteed that there will be at least one valid solution for the given input.

**Example 1:**
```plaintext
Input: groupSizes = [3,3,3,3,3,1,3]
Output: [[5],[0,1,2],[3,4,6]]

Explanation: 
The first group is [5]. The size is 1, and groupSizes[5] = 1.
The second group is [0,1,2]. The size is 3, and groupSizes[0] = groupSizes[1] = groupSizes[2] = 3.
The third group is [3,4,6]. The size is 3, and groupSizes[3] = groupSizes[4] = groupSizes[6] = 3.
Other possible solutions are [[2,1,6],[5],[0,4,3]] and [[5],[0,6,2],[4,3,1]].
```

**Example 2:**
```plaintext
Input: groupSizes = [2,1,3,3,3,2]
Output: [[1],[0,5],[2,3,4]]
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
import java.util.List;
import java.util.ArrayList;
import java.util.HashMap;

public class Solution {

    public static List<List<Integer>> groupThePeople(int[] groupSizes) {
        List<List<Integer>> parentList = new ArrayList();
        HashMap<Integer, ArrayList> hashMap = new HashMap();

        for (int i = 0; i < groupSizes.length; i++) {
            ArrayList<Integer> temp_array;

            if (hashMap.containsKey(groupSizes[i])) {
                temp_array = hashMap.get(groupSizes[i]);
            } else {
                temp_array = new ArrayList<>();
            }

            temp_array.add(i);

            if (temp_array.size() == groupSizes[i]) {
                parentList.add(temp_array);
                hashMap.remove(groupSizes[i]);
            } else {
                hashMap.put(groupSizes[i], temp_array);
            }
        }
        return parentList;
    }
}
```
***
