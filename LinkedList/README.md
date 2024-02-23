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

**Example1:**
```plaintext
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

**Example2:**
```plaintext
Input: head = [1,2]
Output: [2,1]
```

**Example3:**
```plaintext
Input: head = []
Output: []
```



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
