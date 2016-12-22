### 3Sum Closest

Given an array S of n integers, find three integers in S such that the sum is closest to a given number, target. Return the sum of the three integers. You may assume that each input would have exactly one solution.

* 在给定n个整数的数组S，在S中找到三个整数，使得和最接近给定数目target,返回三个整数的和

```
For example, given array S = {-1 2 1 -4}, and target = 1.

The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
```

``` java
public class Solution {
    public int threeSumClosest(int[] nums, int target) {
        int min = Integer.MAX_VALUE;
        int ret = 0;
        Arrays.sort(nums);
        for(int i=0;i<nums.length;i++){
            int i = i+1;
            int k = nums.length-1;
            while(j < k) {
                int sum = nums[i] + nums[j] + nums[k];
                int diff = Math.abs(sum-target);
                if(diff == 0) return sum;
                if(diff < min) {
                    min = diff;
                    ret = sum;
                }
                if(sum <= target) j++;
                else k--;
            }
        }
        return ret;
     }
}
```

``` python
class Solution(object):
    def threeSumClosest(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        nums.sort()
        ret = nums[0]+nums[1]+nums[2]
        length =len(nums)
        for i in range(length-2):
            j, k = i+1, length-1
            while j < k:
                sum = nums[i]+nums[j]+nums[k]
                if sum == target:
                    return sum
                if abs(sum-target)<abs(ret-target):
                    ret=sum
                if sum < target:
                    j+=1
                elif sum > target:
                    k-=1
        return ret
                
```