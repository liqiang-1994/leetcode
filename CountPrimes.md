### Count Primes

Count the number of prime numbers less than a non-negative number, n.
* 计算小于非负数n的素数数量
``` java
public class Solution {
   public int countPrimes(int n) {
    if n<=1 return 0;
    boolean[] notPrime = new boolean[n];
    notPrime[0] = true;
    notPrime[1] = true;
    for(int i=2; i<= Math.sqrt(n);i++) {
        for(int j=2;i*j < n;j++) {
        notPrime[i*j] = true;
     }
     int count=0;
     for(int m=2;m<n;m++) {
         if(!notPrime[m]) {
              count++;
        }
     }
    return count;
    }
}
       
```
``` java
public class Solution {
   public int countPrimes(int n) {
      boolean[] notPrime = new boolean[n];
      int count;
      for(int i=2;i<n;i++) {
           if(notPrime[i] == false) {
               count++;
               for(int  j=2;i*j <n;j++) {
                    notPrime[i*j] = true;
               }
           }
       }
       return  count;
    }
}                   
```
``` java
public class Solution {
    public int countPrimes(int n) {
         boolean[] notPrime = new boolean[n];
         int count=0;
         for(int i=0;i<=Math.sqrt(n);i++) {
               if(notPrime[i]==false){
                      count++;
                      if(i>Math.sqrt(n)){
                        continue;
                            }
                      for(int i=2;i*j <n;j++){
                           notPrime[i*j] = true;
                           }
                    }
              }
          return count;
     }
 }
```
``` python
class Solution(object):
    def countPrimes(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n<=2:
            return 0
        notPrime = [True]*n
        notPrime[0:2] = [False]*2
        for i in range(2:int(n**0.5)+1):
            if notPrime[i] == True:
                notPrime[i*2:n:i] = [False]*((n-1-i*2)/2+1)
        return sum(notPrime)
          
```