### Rotate Array

Rotate an array of n elements to the right by k steps.

For example, with n = 7 and k = 3, the array [1,2,3,4,5,6,7] is rotated to [5,6,7,1,2,3,4].

* 将n个元素的数组向右旋转k个步长，如n=7,k=3时，将数组[1,2,3,4,5,6,7]旋转成[5,6,7,1,2,3,4]

* 思路：先整个逆序排列，再分步前后各排序
``` java
public class Solution {
     public void rotate(int[] nums, int k) {
     k %= nums.length; //避免k大于数组长度出现错误
     
     reverse(nums, 0, nums.length-1); // ==>[7,6,5,4,3,2,1]
     reverse(nums, 0, k-1);                   //==>[5,6,7,4,3,2,1]
     reverse(nums, k, nums.length-1); //==>[,5,6,7,1,2,3,4]
     }
     public void reverse(int[] nums,int start, int end) {
             while(start < end) {
             int temp = nums[start];
             nums[start] = nums[end];
             nums[end] = temp;
             start++;
             end--;
     }
```
* 利用python的pop()从列表尾删除的特性，选择从0处插入
``` python
class Solution(object):
    def rotate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        for i in range(k):
            nums.insert(0, nums.pop())
```
* 下面是利用python的切片的实现了这个算法
``` python
class Solution(object):
    def rotate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        l= len(nums)
        k%=l
        nums[0: l] = nums[l-k: l] +nums[0: l-k]
```
