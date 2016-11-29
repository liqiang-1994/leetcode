### House Robber
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

* 一个专业的强盗计划抢一条街的房子。 每个房子都有一定金额的钱，唯一的约束，阻止你抢劫他们是相邻的房子有安全系统连接，如果两个相邻的房子被打破在同一个夜晚，它会自动联系警察。给出一个表示每个房子的钱数的非负整数列表，返回今晚可以抢夺的最大金额，而不报警。

* 思路：这道题可以看作是在一个数组中取出一个或多个不相邻的数，使其和最大，可以使用动态规划求解，维护一个数组dp，其中dp中的值表示到位置i时不相邻数的最大和，设dp[0]=nums[0], dp[1]设为nums[0], nums[1]中的最大值，dp[2]=max(dp[0]+nums[2], dp[1]), 如果一三位之和大于前两个中的max，则三取1，3，否则取2，依次类推，可推倒出递推公式dp[i]=max(dp[i-2]+nums[i], dp[i-1]),
``` java
public class Solution {
    public int rob(int[] nums) {
        if(nums.length <=1) return (nums.length==0) ? 0 : nums[0];
        int[] mark = new int[nums.length];
        mark[0] = nums[0];
        mark[1] = Math.max(nums[0], nums[1]);
        for(int i=2;i<nums.length;i++) {
            mark[i] = Math.max(nums[i]+mark[i-2], mark[i-1]);
        }
        return mark[nums.length-1];
    }
}
```
* 使用两个变量，按奇偶分别来更新，这样来保证组成的最大和的数子不相邻
``` python
class Solution(object):
    def rob(self, nums):
        """
        :type nums: List[int]
        :rtype : int
        """
        a, b = 0, 0
        for i in xrange(len(nums)):
            if a%2==0:
                a+=nums[i]
                a=max(a,b)
            else:
                b+=nums[i]
                b=max(a,b)
        return max(a,b)
        
```
``` java
public class Solution {
    public int rob(int[] nums) {
        int a=0, b=0;
        for(int i=0;i<nums.length;i++){
            int temp = a > nums[i]+b ? a :b+nums[i];
            b=a;
            a=temp;
        }
        return a;
    }
}
```












