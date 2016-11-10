### Number of 1Bits

Write a function that takes an unsigned integer and returns the number of ’1' bits it has (also known as the Hamming weight).

* 编写一个函数，输入一个无符号整数，返回"1"的位数(又称汉明码权重)

例如，11表示二进制数(00000000000000000000000000001011) return 3.

* 使用Integer类的内建方法bitCount()
``` java
public class Solution {
   //you need to treat n as an unsigned value
   public int hammingWeight(int n) {
      return Integer.bitCount(n);
    }
}
```
``` java
public class Solution {
   public int hammingWeight(int n) {
      int result = 0;
      while(n!= 0) {
         result +=(n&1);
         n = n>>>1;
      }
      return result;
    }
}
```
``` java
public class Solution {
    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        int count =0;
        if(n==0) return 0;
        for(int i=0;i<32;i++){
            if((n&(1<<i))!=0){
                count++;
            }
        }
        return count;
    }
}
```
* 这个是1ms的代码，也是JavaJDK1.8的bitCount()方法的源代码
``` java
public class Solution {
   public int hammingWeight(int n) {
      i = i - ((i>>>1) & 0x55555555);
      i = (i & 0x33333333) + ((i >>>2) &  0x33333333);
      i = (i +(i >>>4)) & 0x0f0f0f0f;
      i = i + (i >>>8);
      i = i +(i >>> 16);
      return i & 0x3f;
    }
}
```
``` python
class Solution(object):
    def hammingWeight(self, n):
        """
        :type n:int
        :rtype :int
        """
        int count
        while n != 0:
            if n &1:
                count+=1
            n = n>>1
        return count
```
