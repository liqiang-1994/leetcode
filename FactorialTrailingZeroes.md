### Factorial Trailing Zeroes

Given an integer n, return the number of trailing zeroes in n!.

* 给定一个整数n，返回n的阶乘后面跟随0的数目

* 思路：所有的0来自因子5*2，因为因子2很多，只需要寻找因子5的个数

``` java
public class Solution {
    public int trailingZeroes(int n) {
        return n==0 ? 0 : n/5+ trailingZeroes(n/5);
```
``` java
public class Solution {
    public int trailingZeroes(int n) {
        int ret = 0;
        while(n>0){
            ret += n/5;
            n/=5;
        }
        return ret;
    }
}
```

``` python
class Solution(object):
    def trailingZeroes(self, n):
        """
        :type n: int
        :rtype: int
        """
        return 0 if n==0 else n/5 + self.trailingZeroes(n/5)
```



