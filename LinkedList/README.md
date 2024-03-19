# Linked Lists

- This directory contains solutions to various programming problems related to linked lists.
- The problems are organized based on the [NeetCode](https://neetcode.io/) roadmap.
- Starting with basic problems, followed by more complex challenges.

## Folder Structure
- [Easy](#easy)
- [Medium](#medium)
- [Hard](#hard)

## Problem Solving Approach

1. **Basic Problems:**
   - Begin with "Easy" problems and gradually progress to "Medium" and "Hard" based on your comfort and confidence.
   - Follow the [NeetCode](https://neetcode.io/) roadmap for a structured learning path.

2. **Advanced Challenges:**
   - Dive into more complex problems from different websites to enhance your problem-solving skills.
   - Tackle problems based on their relevance to specific concepts related to linked lists.

***
## Problems and Solutions

### Easy

#### Problem 1: [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

**Description:**
Given the head of a singly linked list, reverse the list, and return the reversed list.

**Example 1:**
```plaintext
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

**Example 2:**
```plaintext
Input: head = [1,2]
Output: [2,1]
```

**Example 3:**
```plaintext
Input: head = []
Output: []
```


**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
public class Solution {

    /**
     * Definition for singly-linked list. public class ListNode { int val;
     * ListNode next; ListNode() {} ListNode(int val) { this.val = val; }
     * ListNode(int val, ListNode next) { this.val = val; this.next = next; } }
     */
    public ListNode reverseList(ListNode head) {
        if (head == null || head.next == null) {
            return head;
        }

        ListNode prev = head;
        ListNode current = head.next;
        ListNode temp = current;

        prev.next = null;

        while (temp.next != null) {
            temp = temp.next;

            current.next = prev;
            prev = current;
            current = temp;
        }
        current.next = prev;
        return current;
    }
}
```

**Solution (More simple):**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
public class Solution {

    public ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode current = head;

        while (current != null) {
            ListNode nextNode = current.next;
            current.next = prev;
            prev = current;
            current = nextNode;
        }
        return prev;
    }
}
```
***
#### Problem 2: [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

**Description:**
You are given the heads of two sorted linked lists list1 and list2.
Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.
Return the head of the merged linked list.

**Example 1:**
```plaintext
Input: list1 = [1,2,4], list2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

**Example 2:**
```plaintext
Input: list1 = [], list2 = []
Output: []
```

**Example 3:**
```plaintext
Input: list1 = [], list2 = [0]
Output: [0]
```

**Solution:**
```java
/**
 *
 * @author Mohamed Abdalkader
 */
/**
 * Definition for singly-linked list. public class ListNode { int val; ListNode
 * next; ListNode() {} ListNode(int val) { this.val = val; } ListNode(int val,
 * ListNode next) { this.val = val; this.next = next; } }
 */
public class Solution {

    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode temp;
        if (list1 == null) {
            return list2;
        } else if (list2 == null) {
            return list1;
        }

        if (list1.val < list2.val) {
            temp = list1;
            list1 = list1.next;
        } else {
            temp = list2;
            list2 = list2.next;
        }

        ListNode output = temp;

        while (list1 != null && list2 != null) {
            if (list1.val <= list2.val) {
                temp.next = list1;
                list1 = list1.next;
            } else {
                temp.next = list2;
                list2 = list2.next;
            }
            temp = temp.next;
        }
        temp.next = list1 != null ? list1 : list2;
        return output;
    }
}

```
***
### Medium

#### Problem 1: [Reorder List](https://leetcode.com/problems/reorder-list/)

**Description:**
You are given the head of a singly linked-list. The list can be represented as:

L0 → L1 → … → Ln - 1 → Ln
Reorder the list to be on the following form:

L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …
You may not modify the values in the list's nodes. Only nodes themselves may be changed.

**Example 1:**
```plaintext
Input: head = [1,2,3,4]
Output: [1,4,2,3]
```

**Example 2:**
```plaintext
Input: head = [1,2,3,4,5]
Output: [1,5,2,4,3]
```

**Solution:**
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


/**
 *
 * @author Mohamed Abdalkader
 */
import java.util.Stack;

public class Solution {

    Stack<ListNode> stack = new Stack<>();
    int middle_order = 1;
    int stack_size = 0;

    public ListNode findMiddle(ListNode head) {
        if (head == null) {
            return null;
        }

        ListNode slow = head;
        ListNode fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            middle_order++;
        }

        return slow;
    }

    public void reorderList(ListNode head) {

        ListNode middleNode = findMiddle(head); // O(n/2)

        while (middleNode.next != null) { // O(n/2)
            stack.push(middleNode.next);
            middleNode = middleNode.next;
        }

        stack_size = stack.size();

        middleNode.next = null;
        ListNode modifier = head;

        while (!stack.isEmpty()) {
            ListNode temp = modifier.next;
            modifier.next = stack.pop();
            modifier.next.next = temp;
            modifier = modifier.next.next;
        }

        if (stack_size == middle_order - 1) {
            modifier.next = null;
        } else {
            modifier.next.next = null;
        }
    }
}
```
***
#### Problem 2: [Remove Nth Node from End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

**Description:**
Given the head of a linked list, remove the nth node from the end of the list and return its head.

**Example 1:**
```plaintext
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
```

**Example 2:**
```plaintext
Input: head = [1], n = 1
Output: []
```

**Example 3:**
```plaintext
Input: head = [1,2], n = 1
Output: [1]
```

**Solution:**
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

/**
 *
 * @author Mohamed Abdalkader
 */
public class Solution {

    public ListNode removeNthFromEnd(ListNode head, int n) {
        if (head == null || head.next == null) {
            return null;
        }

        ListNode dummy = new ListNode(0);
        dummy.next = head;

        ListNode first = dummy;
        ListNode second = dummy;

        for (int i = 0; i <= n; i++) {
            second = second.next;
        }

        while (second != null) {
            first = first.next;
            second = second.next;
        }

        first.next = first.next.next;

        return dummy.next;
    }
}
```
