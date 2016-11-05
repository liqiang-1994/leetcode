### Happy Number
Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.
* 定义：从任何正整数开始，将数字替换成个十百等位数字的平方和，并重复该过程，直到等于1，即是Happy Number，否则不断在一个不包括1的周期中循环。

* 19是happy number

1<sup>2</sup> + 9<sup>2</sup> =82
8<sup>2</sup> + 2<sup>2</sup> = 68
6<sup>2</sup> + 8<sup>2</sup> = 100
1<sup>2</sup> + 0<sup>2</sup> + 0<sup>2</sup> = 1

* [Happy Number by wilipedia](https://zh.wikipedia.org/wiki/快樂數),不是快乐数的数称为不快乐数，所有不快乐数的数位平方和计算，最后都会进入4-> 16 -> 37 -> 58 -> 89 -> 145 -> 42 ->20 -> 4的循环中。这就是该算法的基础，首先对1和4判断，否则回调isHappy()函数
``` java
public class Solution {
    public boolean isHappy(int n) {
         if(n<=0) {
             return false;
          }else if(n==1) {
              return true;
           }else if(n==4) {
              return false;
           }
           return isHappy(next(n));
       }
     public int next(int n) {
     int result=0;
     while(n>0){
        int temp = n%10;
        result+=temp*temp;
        n=n/10;
     }
      return result;
    }
}
     
```
* 下面是根据集合里的对象唯一存储的特性，首先判断n为1直接返回true，否则进入到不为1时一直循环的while块中，如果set中包含生成的新的n值，说明这个数会在不包含1的周期中循环，不是happy number返回false
``` java
public class Solution {
     public boolean isHappy(int n){
         if(n==1) return true;
         HashSet<integer> set = new HashSet<>();
         while(n !=1){
           if(set.contains(n) {
               return false:
               }
               set.add(n);
               n = next(n);
             }
             if(n ==1){
             return true;
             }
             return false;
          }
      public int next(int n) {
       int result = 0;
       while(n!=0) {
            int temp = n%10;
            result +=temp*temp;
            n =n/10;
          }
        return result;
      }
}       
```
* 下面的python解法和上面第一种解法相同，只不过在分割数字时利用了列表的便捷性
``` python
class Solutiom(object):
    def isHappy(self, n):
    """
    :type n:int
    :rtype:bool
    """
    next = list(str(n))
    result = 0
    if n==1:
         return True
    elif n==4:
         return False
    else:
        for i in next:
            result+=i**2
        return self.isHappy(result) 
           
```