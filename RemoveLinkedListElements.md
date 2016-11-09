### Remove Linked List Elements

Remove all elements from a linked list of integers that have value val.

* 在链表中移除所有值是val的元素

``` 
Given: 1 --> 2 --> 6 --> 3 --> 4 --> 5 --> 6, val = 6
Return: 1 --> 2 --> 3 --> 4 --> 5
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
      public ListNode removeElmenets(ListNode head, int val) {
           ListNode previous = head;
           ListNode current = head;
           
           while(current != null) {
              if(current.val == val) {
                 if(current == head) {
                    head = current.next;
                    previous = head;
                     current = previous;
                  }else {
                   previous.next = current.next;
                   current = previous.next;
                  }
               }else {
               previous = current;
               current = current.next;
           }
         }
         return head;
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
    def removeElments(self, head, val):
        """
        :type head: ListNode
        :type val: int
        :rtype: ListNode
        """
        while head and head.val == val:
            head = head.next
        if not head:
            return head
        prev, current = head, head.next
        while current:
            if current.val ==val:
                prev.next = current.next
                current = prev.next
            else:
                prev,current =current, current.next
        return head 

```