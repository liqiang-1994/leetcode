### Climbing Stairs

You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

* 爬楼梯，需要n步到达顶部，每步可以爬1或2步，有几种到达顶部的方式？

* 思路：爬到第n层的方法要么是从第n-1层一步上来，要不就是从n-2层2步上来，所以递推公式是dp[n]=dp[n-1]+dp[n-2],不过递归在leetcode上是超时的

``` java
public class Solution {
    public int climbStairs(int n){
        if(n<=1) return 1;
        return climbStairs(n-1)+climStairs(n-1);
      }
}

public class Solution {
    public int climbStairs(int n){
        if(n<1) return 0;
        if(n==1 || n==2) return n;
        return climbStairs(n-1) + climbStairs(n-2);
      }
 }
```

* 使用动态规划解决
``` java
public class Solution {
    public int climbStairs(int n) {
        if(n<=1) return 1;
        int[] climb = new int[n+1];
        climb[0]=1;
        climb[1]=1;
        for(int i=2;i<=n;i++){
            climb[i]=climb[i-1]+climb[i-2];
          }
          return climb[n];
     }
}
```
* 斐波那契数列：0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ...,即斐波那契数列的n项值是第n层爬楼梯的爬法的种类数
``` python
class Solution(object):
    def climbStairs(self, n):
        """
        :type n:int 
        :rtype: int
        """
        a=0
        b=1
        for i in range(1,n+1,1):
            sum = a+b
            a=b
            b=sum
        return sum
 * 更加优雅的写法
 class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        a, b = 0,1
        for i in range(n):
            a,b = b, a+b
        return b
```