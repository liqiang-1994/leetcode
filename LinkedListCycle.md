### Linked List Cycle

Given a linked list, determine if it has a cycle in it.

* 判断链表是否有一个循环

``` java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        if(head==null) return false;
        while(head.next!=null && head.next!=head) {
            ListNode temp = head.next;
            head.next = head.next.next;
            head = temp;
        }
        return head.next !=null;
      }
 }
```
* 设置两个指针，一个跑地快，一个跑的慢，如果ListNode成环，必定慢指针会追上快指针
``` java
public class Solution {
     public boolean hasCycle(ListNode head) {
         if(head==null) return false;
         ListNode prev = head;
         ListNode cur = head;
         while(prev !=null && prev.next!=null) {
             prev = prev.next.next;
             cur = cur.next;
             if(prev ==cur) return true;
          }
          return false;
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
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        pre, cur = head, head
        while pre and pre.next:
            pre = pre.next.next
            cur = cur.next
            if cur==pre:
                return True
        return False
```