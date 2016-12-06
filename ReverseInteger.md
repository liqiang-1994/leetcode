### Reverse Integer

Reverse digits of an integer

``` 
Example1: x = 123, return 321
Example2: x = -123, return -321
```
* 反向输出Intger

``` java
public class Solution {
    public int reverse(int x) {
        int result = 0;
        while( x!=0) {
            int tail = x %10;
            int temp = result *10 +tail;
            if((temp - tail)/10 != result) return 0; //如果不相等则说明溢出
            result = temp;
            x/=10;
        }
        return result;
    }
} 
```
``` java
public class Solution {
    public int reverse(int x) {
    long ret =0;
    while(x!=0) {
        ret = ret*10 +x%10;
        if(ret>Integer.MAX_VALUE || ret<Integer.MIN_VALUE) return 0;
        x/=10;
     }
     return (int)ret;
   }
}
```
* repr()函数就是创建一个字符串，以合适的Python表达式的形式表达值
``` python
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        s = cmp(x,0)
        ret = int(repr(x*s)[::-1])
        return ret*s*(ret<2**31)
        
```