### Multiply Strings

Given two numbers represented as strings, return multiplication of the numbers as a string.

The numbers can be arbitrarily large and are non-negative.//数字时任意大且非负
Converting the input string to integer is NOT allowed.//不允许将输入的字符串转化为整数
You should NOT use internal library such as BigInteger.//不应该使用内部库
Subscribe to see which companies asked this question

* 给定两个字符串表示的数字，返回数字的乘法作为字符串

``` java
public class Solution {
    public String multiply(String num1, String num2) {
        int m=num1.length(), n=num2.length();
        int[] ret = new int[m+n];
        
        for(int i=m-1;i>=0;i--){
            for(int j=n-1;j>=0;j--){
                int temp=(num1.charAt(i)-'0')*(num2.charAt(j)-'0');
                int prev=i+j, last=i+j+1;
                int sum = temp+ret[last];
                ret[prev]+=sum/10;
                ret[last]=(sum)%10;
            }
        }
        StringBuilder sb = new StringBuilder();
        for(int p : ret) if(!(sb.length()==0 && p==0)) sb.append(p);
        return sb.length()==0 ? "0" : sb.toString();
    }
}
```