### Intersection of Two Linked Lists

Write a program to find the node at which the intersection of two singly linked lists begins.

* 找到两个单链表的交集开始的地方

``` 
A:          a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3

If the two linked lists have no intersection at all, return null. //如果两个链表没有交集，返回null
The linked lists must retain their original structure after the function returns.//链表在返回后保留原始结构
You may assume there are no cycles anywhere in the entire linked structure.//假定整个链表结构没有任何循环
Your code should preferably run in O(n) time and use only O(1) memory.
```
* 使用两次迭代，在第一次迭代中长度小的链表首先完成，然后将链表的指针重值为长链表的头，等到长链表完成后，重值为短链表的头，利用查值消除长度差异
``` java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
 public class Solution {
     public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
         if(headA==null || headB==null) return null;
         ListNode p = headA;
         ListNode q = headB;
         while(p != q) {
             p = p==null ? headB : p.next;
             q = q==null ? headA : q.next;
         }
         return p;
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
    def getIntersectionNode(self, headA, headB):
        """
        :type head1, head1: ListNode
        :rtype: ListNode
        """
        if headA is None or headB is None:
            return None
        p = headA
        q=headB
        while p is not q:
            p = q if p is None else p.next
            q = p if q is None else q.next
        return p
```