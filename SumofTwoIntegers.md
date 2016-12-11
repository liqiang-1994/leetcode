### Sum of Two Integers

Calculate the sum of two integers a and b, but you are not allowed to use the operator + and -.

* 不用加减运算符计算两个整数的和

``` java
public class Solution {
    public int getSum(int a, int b) {
        int sum = a ^ b;
        int up = (a & b)<< 1;
        while(up != 0) {
            return getSum(sum, up);
        }
        return sum;
    }
}
```
``` java
public class Solution {
    public int getSum(int a, int b) {
        if(a==0) return b;
        if(b==0) return a;
        while(b!=0){
            int up=a&b;
            a=a^b;
            b= up<<1;
        }
        return a;
    }
}
```
``` java
public int getSum(int a, int b) {
	return (b == 0) ? a : getSum(a ^ b, (a & b) << 1);
}
```