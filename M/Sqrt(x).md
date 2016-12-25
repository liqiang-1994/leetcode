### Sqrt(x)

Implement int sqrt(int x).Compute and return the square root of x.

* 实现平方根算法

``` java
public class Solution {
    public int mySqrt(int n) {
        if(n==0) return 0;
        int left = 1, right = Integer.MAX_VALUE;
        while(true) {
            int mid = left +(right-left)/2;
            if(mid >n /mid) right =mid-1;
            else {
                if((mid+1)>n/(mid+1)) return mid;
                left=mid+1;
            }
       }
    }
}
```
* | 位或的本质是把这个数变为最接近这个数的偶数
* & 位与可以用来判断一个整数的奇偶性
* ^ 用于对二进制的特定一位进行取反操作,同一个数异或结果不变

``` java
public class Solution {
    public int mySqrt(int x) {
        if(x==0) return 0;
        int h=0;
        while((long)(1<<h) * (long)(1<<h)<=x) h++;
        h--;
        int b=h-1;
        int ret = 1<<h;
        while(b>=0) { 
            if((long)(ret | (1<<b)) * (long)(ret | (1<<b))<=x) ret|=(1<<b);
            b--;
        }
        return ret;
    }
}
```

``` java
public class Solution {
    public int mySqrt(int x) {
        long ret=0;
        long bit = 1l << 16;
        while(bit>0){
            ret |= bit;
            if(ret*ret>x) ret^=bit;
            bit>>=1;
        }
        return (int)ret;
    }
}
```