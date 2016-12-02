### Delete Node in a Linked List

Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.

Supposed the linked list is 1 -> 2 -> 3 -> 4 and you are given the third node with value 3, the linked list should become 1 -> 2 -> 4 after calling your function.

* 编写一个函数删除单链表中的一个节点(尾部除外)，只给定该节点的访问权限.假设链表是 1->2->3->4,给出第三个节点的值为3，链表在调用函数后因该变成1->2->4

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
     public void deleteNode(ListNode node) {
         if(node !=null && node.next !=null) {
             node.val = node.next.val;
             node.next = node.next.next;
          }
     }
}
```
* 给定节点不是尾部节点，上面可简化如下
``` python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        node.val = node.next.val
        node.next = node.next.next
```