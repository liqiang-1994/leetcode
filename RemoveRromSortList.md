
##### Remove Duplicates from Sorted List
Given a sorted linked list, delete all duplicates such that each element appear only once.

For example,
Given 1->1->2, return 1->2.
Given 1->1->2->3->3, return 1->2->3.

* 给定一个排序的列表，删除重复的元素使每个元素只出现一次
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
    public ListNode deleteDuplicates(ListNode head) {
        if(head == null){
            return null;
         }
        if(head.next != null && head.next.val == head.val) {
            head.next = head.next.next;
            head = deleteDuplicates(head);
            }else{
            head.next = deleteDuplicates(head.next);
            }
        return head;
      }
}                
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
    public ListNode deleteDuplicates(ListNode head) {
    if(head == null || head.next == null) return head;
    ListNode node = head;
    while(node.next != null) {
       if(node.val ==node.next.val){
             node.next = node.next.next;
           }else{
              node = node.next;
            }
        sreturn head;
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
    def deleteDuplicates(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if head == None or head.next == None:
            return head;
        node = head
        while(node.next != None):
            if node.val == node.next.val:
                node.next = node.next.next;
            else:
                node = node.next
        return head
```
