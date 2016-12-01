### Contains Duplicate

Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

* 给定一个整数数组，判断该数组是否包含任何重复，如果该数组的任何一个或多个值在数组中至少出现两次，则函数应返回true, 如果每个元素都不相同，则返回false

* 思路：经过排序的数组，如果有相邻两个数组相等，即返回true
``` java
public class Solution {
    public boolean containsDuplicate(int[] nums) {
        if(nums.length <=1)  return false;
        Arrays.sort(nums);
        for(int i=0;i<nums.length-1;i++) {
            if(nums[i]==nums[i+1]) {
                return true;
            }
         }
         return false;
     }
 }
```
* 使用HashSet
``` java
public class Solution {
    public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        for(int n:nums){
            if(set.contains(n)) {
                return true;
            }
            set.add(n);
          }
          return false;
      }
}
```

``` python
class Solution(object):
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        if len(nums) <1:
            return False
        return len(nums) != len(list(set(nums)))
```