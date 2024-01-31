#### Problem 1: [Range Sum Query - Immutable](https://leetcode.com/problems/range-sum-query-immutable/)

**Description:**

Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].
The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.
You must write an algorithm that runs in `O(n)` time and without using the division operation.

**Example 1:**
```plaintext
Input
["NumArray", "sumRange", "sumRange", "sumRange"]
[[[-2, 0, 3, -5, 2, -1]], [0, 2], [2, 5], [0, 5]]
Output
[null, 1, -1, -3]

Explanation
NumArray numArray = new NumArray([-2, 0, 3, -5, 2, -1]);
numArray.sumRange(0, 2); // return (-2) + 0 + 3 = 1
numArray.sumRange(2, 5); // return 3 + (-5) + 2 + (-1) = -1
numArray.sumRange(0, 5); // return (-2) + 0 + 3 + (-5) + 2 + (-1) = -3
```

**Solution 1:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
class NumArray {
    int[] nums;
    public NumArray(int[] nums) {
        this.nums = nums;
        
    }
    
    public int sumRange(int left, int right) {
        int sum = 0;
        for(int i=left; i <= right; i++){
            sum += nums[i];
        }
        return sum;
    }
}
```

**Solution 2:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
class NumArray {
    int[] prefix_sum;
    public NumArray(int[] nums) {
        int sum = 0;
        prefix_sum = new int[nums.length];

        for(int i=0; i < nums.length; i++){
            sum += nums[i];
            prefix_sum[i] = sum;
        }
    }
    
    public int sumRange(int left, int right) {
        if(left != 0){
            return prefix_sum[right]-prefix_sum[left-1];
        }
        return prefix_sum[right];
    }
}
```
***
