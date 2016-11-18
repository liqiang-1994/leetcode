### Ugly Number

Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 6, 8 are ugly while 14 is not ugly since it includes another prime factor 7.

* 如果一个数是正数，且它的素因子只有2，3，5则是Ugly Number，6and 8是，14则不是，因为它包括另一个素因子7。1被看作Ugly Number.

* 思路：如果该数对2或3或5取余等于0，则用它除以2或3或5，如果素因子有2，3，5即返回 true
``` java
public class Solution {
   public boolean isUgly(int num) {
      if(num == 0) return false;
      if(num == 1) return true;
      boolean two = false;
      boolean three = false;
      boolean five = flase;
      if(num %2 ==0) {
         two = isUgly(num/2);
      }
      if(num % 3==0) {
         three = isUgly(num/3);
      }
      if(num %A 5 ==0) {
         five = isUgly(num/5);
      }
      return (two || three || five);
   }
 }
```

``` java
public class Solution {
    public boolean isUgly(int num) {
        while(num < 1) return false;
        num = next(num,2);
        num = next(num,3);
        num  = next(num,5);
        return num ==1;
    }
    
    public int next(int num, int n) {
        while(num%n==0){
            num = num/n;
        }
        return num;
    }
}
```

``` java
class Solution(object):
    def isUgly(self, num):
        """
        :type num: int 
        :rtype: bool
        """
        if num ==0:
            return False
        if num ==1:
            return True
        while num%2==0:
            num = num>>1
        while num%3==0:
            num = num/3
        while num%5==0:
            num = num/5
        return num==1  
```