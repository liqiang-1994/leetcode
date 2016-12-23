### Pow(x, n)

* Implement pow(x, n)

* 当n等于INT_MIN时，求绝对值之后会超出整数范围，因为负数是比正数多一个
``` java
public class Solution {
    public double myPow(double x, int n) {
        if(n==0) return 1;
        if(n==Integer.MIN_VALUE) {
            x=x*x;
            n=n/2;
         }
         if(n<0) {
             n= -n;
             x=1/x;
          }
          return (n%2==0) ? myPow(x*x, n/2) : x*myPow(x*x, n/2);
       }
 }
```

``` java
public class Solution {
    public double myPow(double x, int x) {
        if(n==0) return 1;
        double pow = myPow(x, n/2);
        if(n%2==0) return pow*pow;
        return (n<0) ? pow*pow/x : pow*pow*x;
     }
 }
```
``` python
class Solution(object):
    def myPow(self, x, n):
        """
        :type x: float
        :type n: int
        :rtype: float
        """
        if not n:
            return 1
        if n<0:
            return 1.0/self.myPow(x, -n)
        if n%2:
            return x*self.myPow(x, n-1)
        return self.myPow(x*x, n/2)
```
``` python
class Solution(object):
    def myPow(self, x, n):
        """
        :type x: float
        :type n: int
        :rtype: float
        """
        if n<0:
            x=1/x
            n=-n
        pow=1
        while n:
            if n&1:
                pow*=x
            x*=x
            n>>=1
        return pow
```
``` java
public class Solution {
    public double myPow(double x, int n) {
        long m = n>0 ? n : -(long)n;
        double ret=1.0;
        while(m!=0){
            if((m&1)==1) ret*=x;
            x*=x;
            m>>=1;
        }
        return n>=0 ? ret : 1/ret;
    }
}
```