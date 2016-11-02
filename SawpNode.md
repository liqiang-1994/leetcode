### Swap Nodes in Pairs
Given a linked list, swap every two adjacent nodes and return its head.

For example,
Given 1->2->3->4, you should return the list as 2->1->4->3.

Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.

* 给定一个链表，交换相邻两个节点并返回头节点
例如 给出1->2->3->4, 返回2->1->4->3

思路：通过交换前后两个节点，迭代的交换下下个节点
``` java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
public class Solution {
          public ListNode swapPairs(ListNode head) {
             if(head != null && head.next != null) {
                 ListNode temp = head.next.next;
                 ListNode next = head.next;
                 next.next = head;
                 next.next.next = swapPairs(temp);
                 return next;
                 }
              return head;
      }
```