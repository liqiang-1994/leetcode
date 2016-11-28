### Power of Two

Given an integer, write a function to determine if it is a power of two.

* 给定一个整数，判断一个数是否是2的幂

``` java
public class Solution {
     public boolean isPowerOfTwo(int n) {
         if(n<=0) return false;
         while((n&1) !=1) {
             n=n>>1;
         }
         return n==1;
     }
}
```
``` java
public class Solution {
   public boolean isPowerOfTwo(int n) {
       return n>0 && (n&(n-1))==0;
   }
}
```