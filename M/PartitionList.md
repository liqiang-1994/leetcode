### Partition List

Given a linked list and a value x, partition it such that all nodes less than x come before nodes greater than or equal to x.You should preserve the original relative order of the nodes in each of the two partitions.

* 给定链接列表和值x，将其分区，使得小于x的所有节点在大于或等于x的节点之前，同时维持两个分区中原始节点的相对顺序

``` 
Given 1->4->3->2->5->2 and x = 3,
return 1->2->2->4->3->5.
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
    public ListNode partition(ListNode head, int x) {
        ListNode ret1 = new ListNode(0), ret2 = new ListNode(0);
        ListNode cur1 = ret1, cur2 = ret2;
        while(head!=null){
            if(head.val < xl){
                cur1.next=head;
                cur1=head;
             }else{
                 cur2.next=head;
                 cur2=head;
             }
             head=head.next;
         }
         cur2.next=null;
         cur1.next=ret2.next;
         return ret1.next;
      }
 }
             
```
