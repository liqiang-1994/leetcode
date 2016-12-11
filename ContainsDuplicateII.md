### Contains Duplicate II

Given an array of integers and an integer k, find out whether there are two distinct indices i and j in the array such that nums[i] = nums[j] and the difference between i and j is at most k.

* 给定一个整数数组，找出在数组存在两个不同索引i和j，使得nums[i] ==nums[j]并且i和j最大值为k

* 思路：始终使set中保持k个值，若添加失败，说明set中有相同值
``` java
public class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        Set<Integer> set = new HashSet<>();
        for(int i=0;i<nums.length;i++) {
            if(i>k) set.remove(nums[i-k-1]);
            if(!set.add(nums[i])) return true;
        }
        return true;
    }
 }
```
* 利用hashMap求解
``` python
class Solution(object):
    def containsNearbyDuplicate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: bool
        """
        d = {}
        for i in range(len(nums)):
            if d.has_key(nums[i]):
                if i - d.get(nums[i]) <=k:
                    return True
            d[nums[i]] = i
        return False
```