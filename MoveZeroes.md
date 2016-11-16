### Move Zeroes
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

* 给定一个数组nums，写一个函数将所有的0移动到数组末尾，同时保持非零元素的相对数序

``` 
Input :nums = [0,1,0,3,12]
After  : nums = [1,2,12,0,0]
```

``` java
public class Solution {
    public void moveZeroes(int[] nums) {
        if(nums == null || nums.length ==0){
            return;
        }
        for (int i=0;i<nums.length;i++) {
            for (int j=i+1;j<nums.length;j++) {
                if(nums[i] ==0 && nums[j]!= 0) {
                    int temp = nums[j];
                    nums[j] = nums[i];
                    nums[i] = temp;
                }
            }
        }
    }
}
```
``` java
public class Solution {
    public void moveZeroes(int[] nums) {
        for(int i =0;i<nums.length;i++) {
            if(nums[i] !=0) {
                continue;
            }else{
                for(int j=i+1;j<nums.length;j++){
                    if(nums[j]!=0) {
                        int temp = nums[i];
                        nums[i]=nums[j];
                        nums[j]=temp;
                        break;
                    }
                }
            }
        }
    }
}      
```
* java 0ms

``` java
public class Solution {
   public void moveZeroes(int[] nums) {
      int count =0;
      for(int i=0;i<nums.length;i++) {
         if(nums[i]==0) count++;
         else if(count!=0) nums[i-count] = nums[i];
      }
      while(count>0) {
         nums[nums.length-count] =0;
         count--;
       }
   }
}
```
* 前面的解法都是计算为0数组的个数，下面记录不为0的数组个数
``` python
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        count = 0
        for i in range(len(nums)):
            nums[count] = nums[i]
            if nums[i] != 0:
                count+=1
        nums[count:] = [0]*(len((nums)-count)
      
```