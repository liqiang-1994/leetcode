### Rotate List

Given a list, rotate the list to the right by k places, where k is non-negative.

* 将给定列表向右旋转k个,k是非负数

``` 
Given 1->2->3->4->5->NULL and k = 2,
return 4->5->1->2->3->NULL.
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
    public ListNode rotateRight(ListNode head, int k) {
        if(head==null || head.next==null) return head;
        ListNode ret = new ListNode(0);
        ret.next = head;
        ListNode fast=ret, slow=ret;
        int i;
        for(int i=0;fast.next!=null;i++) fast=fast.next;
        for(int j=i-k%i;j>0;j--) slow=slow.next;
        
        fast.next = ret.next;
        ret.next = slow.next;
        slow.next=null
        return ret.next;
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
    public ListNode rotateRight(ListNode head, int k) {
        if(head==null || head.next==null) return head;
        ListNode fast=head, slow=head;
        int i=1;
        while(fast.next != null){
            i++;
            fast=fast.next;
        }
        for(int j=i-k%i;j>1;j--) slow=slow.next;
        fast.next = head;
        head = slow.next;
        slow.next = null;
        return head;
     }
}
```