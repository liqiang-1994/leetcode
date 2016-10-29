
#### Merge Sorted Array
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

Note:
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number of elements initialized in nums1 and nums2 are m and n respectively.

* 给定两个已经排好序的数组nums1和nums2，将nums2和nums2重新排序合并为nums1。假设nums1有足够的空间（大于或等于m + n的大小）来容纳nums2中的其他元素。 在nums1和nums2中初始化的元素的数量分别为m和n。

* 思路：在数组nums1的n+m-1处输入经过比较的数值
``` java
public class Solution {
     public void merge(int[] nums1, int m, int[] nums2, int n) {
         int i=m-1;
         int j=n-1;
         int k= n+m -1;
         while(i>=0 && j>=0) {
           if(nums1[i]>nums2[j]) {
                nums1[k--] = nums1[i--];
            }else{
                nums1[k--] = nums2[j--];
             }
            while(j>=0){
                nums1[k--] = nums2[j--];
            }
    }
  }               
```

``` python
class Solution(object):
     def merge(self, nums1, m, nums2, n):
          """
          :type nums1: List[int]
          :type m: int
          :type nums2: List[int]
          :type n: int
          :rtype: void Do not return anything,modify nums1 in-place insted.
          """
         while n > 0: //如果nums2比较完，则退出不再进行比较
            if m <=0 or nums1[m-1] <nums2[n-1]: //若nums1比较完，则直接将nums2的数值直接复制到nums1中
                nums1[n+m-1] = nums2[n-1]
                n-=1
            else:
                nums1[m+n-1] = nums1[m-1]       
```
* 下面这种比较pythoner，用到了切片
``` python
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: void Do not return anything, modify nums1 in-place instead.
        """
        while n >o and m> 0:
            if nums1[m-1] > nums2[n-1]:
                nums1[n+m-1] = nums1[m-1]
                m-=1
            else:
                nums1[n+m-1] = nums2[n-1]
                n-=1
        if n > 0:
            nums1[: n] = nums2[: n]
```