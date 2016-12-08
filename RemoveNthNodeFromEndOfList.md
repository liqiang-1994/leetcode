###  Remove Nth Node From End of List

Given a linked list, remove the nth node from the end of list and return its head.

* 给定一个链表，从列表的末尾删除第n个节点并返回它的头

```
   Given linked list: 1->2->3->4->5, and n = 2.

   After removing the second node from the end, the linked list becomes 1->2->3->5.
```

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
     public ListNode removeNthFromEnd(ListNode head, int n) {
         ListNode start = new ListNode(0);
         start.next = head;
         ListNode slow = start;
         ListNode fast = start;
         while(n>0){
             fast = fast.next;
             n--;
         }
         while(fast.next!=null){
             fast = fast.next;
             slow = slow.next;
         }
         slow.next = slow.next.next;
         return start.next;
     }
 }    
```
``` python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: ListNode
        :type n: int
        :rtype: ListNode
        """
        def remove(head):
            if not head:
                return 0, head
            i, head.next = remove(head.next)
            return i+1, (head, head.next)[i+1==n]
        return remove(head)[1] 
```
[python解法](https://discuss.leetcode.com/topic/14692/3-short-python-solutions)