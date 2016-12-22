### Add Two Numbers

You are given two linked lists representing two non-negative numbers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

* 由两个非负数的链表，数字以相反的数序存储，并且它们的每个节点包含单个数字，添加两个数字并将其作为链表列表返回 

```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
```
*

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
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode c1 = l1;
        ListNode c2 = l2;
        ListNode ret = new ListNode(0);
        ListNode temp = ret;
        int sum=0;
        while( c1!=null || c2!=null) {
            sum/=10;
            if(c1!=null){
                sum+=c1.val;
                c1=c1.next;
            }
            if(c2!=null){
                sum++c2.val;
                c2=c2.next;
            }
            temp.next = new ListNode(sum%10);
            temp = temp.next;
         }
        if(sum/10==1) temp.next = new ListNode(1);
        return ret.next;
     }
}
            
```

``` java
public class Solution {
    Public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode prev = new ListNode(0);
        ListNode head = prev;
        int carry = 0;
        while(l1 !=null || l2!=null || carry !=0) {
            ListNode current = l1!=null ? l1 : (l2!=null ? l2 : (new ListNode(0)));
            int sum = (l1==null ? 0 : l1.val) + (l2==null ? 0 : l2.val) + carry;
            current.val = sum%10;
            carry = sum/10;
            prev.next = current;
            prev = prev.next;
            
            l1 = (l1==null) ? l1 : l1.next;
            l2 =(l2==null) ? l2 : l2.next;
        }
        return head.next;
     }
}
```