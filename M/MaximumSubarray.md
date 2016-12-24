### Maximum Subarray

Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

For example, given the array [-2,1,-3,4,-1,2,1,-5,4],
the contiguous subarray [4,-1,2,1] has the largest sum = 6.

* 在数组中找到具有最大和的连续子数列(至少包含一个数字)

```

For example, given the array [-2,1,-3,4,-1,2,1,-5,4],
the contiguous subarray [4,-1,2,1] has the largest sum = 6
```

``` java
public class Solution {
    public int maxSubArray(int[] nums) {
    int max =nums[0], maxCur =nums[0];
    for(int i=1;i<nums.length;i++) {
        maxCur = Math.max(maxCur+nums[i], nums[i]);
        max = Math.max(max, maxCur);
    }
    return max;
  }
}
```

``` python
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        dp =[0]*len(nums)
        dp[0] = nums[0]
        m = dp[0]
        for i in range(1, len(nums)):
            dp[i] = nums[i] +dp[i-1] if dp[i-1]>0 else nums[i]
            m = max(dp[i], m)
        return m
```