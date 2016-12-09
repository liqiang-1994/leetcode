### Remove Element

Given an array and a value, remove all instances of that value in place and return the new length.

Do not allocate extra space for another array, you must do this in place with constant memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

* 给定数组和值，原位删除该值所有的实例，并返回新长度。不要为另一个数组分配额外的空间使用常量内存做到这一点

```
Given input array nums = [3,2,2,3], val = 3

Your function should return length = 2, with the first two elements of nums being 2.
```

``` java
public class Solution {
    public int removeElement(int[] nums, int val) {
        int i=0;
        for(int n:nums) {
            if(n!=val){
                nums[i++]=n;
            }
         }
         return i;
     }
}
```

``` python
class Solution(object):
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        start, end = 0, len(nums)-1
        while start<=end:
            if nums[start]==val:
                nums[start], nums[end], end = nums[end], nums[start], end-1
            else:
                start+=1
        return start
```