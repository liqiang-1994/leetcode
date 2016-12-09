### Remove Duplicates from Sorted Array

Given a sorted array, remove the duplicates in place such that each element appear only once and return the new length.Do not allocate extra space for another array, you must do this in place with constant memory.

```
Given input array nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively. It doesn't matter what you leave beyond the new length.
```
* 给定排好序的数组，删除重复的位置，使每个元素只出现一次并返回新的长度

``` java
public class Solution {
    public int removeDuplicates(int[] nums) {
        if(nums.length<2) return nums.length;
        int count =1;
        for(int i=1;i<nums.length;i++){
            if(nums[i] != nums[i-1]) nums[count++] = nums[i];
        }
        return count;
      }
  }
```

```python
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 0
        count=0
        for i in range(1, len(nums)):
            if nums[i]!=nums[count]:
                count+=1
                nums[count]=nums[i]
        return count+1
```

``` java
public class Solution {
    public int removeDuplicates(int[] nums) {
        int i=0;
        for(int n:nums){
            if(i==0 || n>nums[i-1]){
                nums[i++]=n;
            }
        }
        return i;
    }
}
```