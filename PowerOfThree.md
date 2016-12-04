### Power of Three

Given an integer, write a function to determine if it is a power of three. 

* 判断给定的Intger是否是3的次幂

* 使用递归
``` java
public class Solution {
    public boolean isPowerOfThree(int n) {
        return n>0 && (n==1 || (n%3==0 && isPowerOfThree(n/3)));
     }
 }
```
* 使用循环
``` java
public class Solution {
    public boolean isPowerOfThree(int n) {
        if(n>0)  {
            while( n%3==0) {
                n=n/3;
             }
          }
         return n==1;
       }
  }
```
``` java
public class Solution {
    public boolean isPowerOfThree(int n) {
        return n>0 && Math.pow(3, 19)%n==0;
    }
}
```

