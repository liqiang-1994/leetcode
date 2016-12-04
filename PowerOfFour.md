### Power of Four

Given an integer (signed 32 bits), write a function to check whether it is a power of 4.

* 判断给定数是否是4的次幂
```
Given num = 16, return true. Given num = 5, return false.
```

* 此题和Power of Three相同
``` java
public class Solution {
    public boolean isPowerOfFour(int num) {
         return num>0 && (num==1 || (num%4==0 && isPowerOfFour(num/4)));
      }
 }
```
``` java
public class Solution {
    public boolean isPowerOfFour(int num) {
        while(num>0 && (num%4==0)){
            num=num/4;
        }
        return num==1;
    }
}
```
``` java
public class Solution {
    public boolean isPowerOfFour(int num) {
        return Integer.toString(num, 4).matches("10*");//将给定数转化为4进制
    }
}
```

``` java
public class Solution {
    public boolean isPowerOfFour(int num) {
        return num>0 && (num&(num-1))==0 && (num&(0x55555555))==num;
        //先判断num是否是二的次幂，再确定4的次幂都是偶数个0，只需和0x55555555（1010101010101010101010101010101 二进制）相与去掉2的权位，使得1总是在奇数位，位与之后仍是本身
    }
}
```
``` java
public class Solution {
    public boolean isPowerOfFour(int num) {
        return num>0 && (num&(num-1))==0 && (num-1)%3==0;
    }
}
```

