### Decode Ways

A message containing letters from A-Z is being encoded to numbers using the following mapping:

```
'A' -> 1
'B' -> 2
...
'Z' -> 26

Given encoded message "12", it could be decoded as "AB" (1 2) or "L" (12).

The number of ways decoding "12" is 2.
```
* 如果当前数字为0，则前面数字必为1或者2，否则无法进行编码转换，此时的数字0只能和前面的1或者2连在一起进行编码，因此dp[i] = dp[i-2]；
如果前面数字为1或者前面数字为2且当前数字在1~6之间，说明都可以进行2种编码（分开或者和在一起），因此dp[i] = dp[i-1] + dp[i-2]；
其他情况，当前数字必须单独进行编码转换，因此dp[i] = dp[i-1]。
``` java
public class Solution {
    public int numDecodings(String s) {
        int n=s.length();
        if(n==0) return 0;
        int[] ret = new int[n+1];
        ret[n]=1;
        ret[n-1]=s.charAt(n-1)=='0' ? 0 : 1;
        for(int i=n-2;i>=0;i--){
            if(s.charAt(i)=='0') continue;
            else ret[i]=(Integer.parseInt(s.substring(i,i+2))<27) ? ret[i+1]+ret[i+2] : ret[i+1];
        }
        return ret[0];
    }
}
```