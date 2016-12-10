### Add Binary

Given two binary strings, return their sum (also a binary string).

* 给定两个二进制数的字符串，同样以二进制字符串返回它们的和

```
a = "11"
b = "1"
return "100"
```

``` java
public class Solution {
    public String addBinary(String a, String b) {
        if(a==null || b.isEmpty()) return b;
        if(b==null || b.isEmpty()) return a;
        
        int aL = a.length()-1;
        int bL = b.length()-1;
        int aBit;
        int bBit;
        int up = 0; //进位表示符
        int result = 0;
        StringBuilder sb = new StringBuilder();
        while(aL>=0 || bL>=0 || up==1){
            aBit = (aL>=0) ? Character.getNumericValue(a.charAt(aL--)) : 0;
            bBit = (bL>=0) ? Character.getNumericValue(b.charAt(bL--)) : 0;
            result = aBit ^ bBit ^ up;
            up = ((aBit+bBit+up)>=2) ? 1 : 0;
            sb.append(result);
        }
        return sb.reverse().toString();
    }
}
```

``` java
public class Solution {
    public String addBinary(String a, String b) {
        StringBuilder sb = new StringBuilder();
        int up = 0;
        for(int i=0;i<Math.max(a.length(), b.length()) || up !=0;i++){
            int aBit = (i>=a.length()) ? 0 : a.charAt(a.length()-i-1)-'0';
            int bBit = (i>=b.length()) ? 0 : b.charAt(b.length()-i-1)-'0';
            sb.insert(0, (aBit^bBit^up));
            up = (aBit+bBit+up)/2;
        }
        return sb.toString();
    }
}
```

``` python 
class Solution(object):
    def addBinary(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        if len(a)==0:
            return b
        if len(b)==0:
            return a
        if a[-1] =='1' and b[-1]=='1':
            return self.addBinary(self.addBinary(a[0:-1], b[0:-1]), 1) + '0'
        elif a[-1]=='0' and b[-1]=='0':
            return self.addBinary(a[0:-1], b[0:-1])+'0'
        else:
            return self.addBinary(a[0:-1], a[0:-1])+'1'
```
