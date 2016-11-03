### Reverse Linked List
Reverse a singly linked list.

* 反转单链表如 a->b->c->d反转后即是d->c->b->a
* 下面的方法是通过迭代的遍历链表，依次调整顺序，每次遍历先保存next的值后再更新next的值，preNode是前向指针，nextNode是后向指针
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
   public ListNode reverseList(ListNode head) {
      ListNode preNode = null;
      ListNode nextNode = null;
      while(head != null) {
          nextNode = head.next;
          head.next = preNode;
          preNode = head;
          head = nextNode;
          }
          return preNode;
     }
}
```
* 下面的方法是通过递归实现的，利用递归走到链表的尾端，依次再更新next的值
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
   public ListNode reverseList(ListNode head) {
      if(head == null || head.next ==null) {
        return head;
       }
      ListNode nextNode = head.next;
      head.next =null;
      ListNode current = reverseList(nextNode);
      nextNode.next = head;
      return current;
    }
}
```
* 此方法与上面第一种方法相同
``` python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        preNode = None
        while head:
            nextNode = head.next
            head.next = preNode
            preNode = head
            head = nextNode
        return preNode
```