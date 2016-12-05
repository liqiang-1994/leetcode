###  Excel Sheet Column Number

Given a column title as appear in an Excel sheet, return its corresponding column number.

``` 
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
```
``` java
public class Solution {
    public int titleToNumber(String s) {
        int ret =0;
        for(int i=0;i<s.length();i++){
            ret = ret*26+(s.charAt(i)-'A'+1);
        }
        return ret;
    }
}
```
``` java
public class Solution {
    public int titleToNumber(String s) {
        int ret =0;
        for(int i=0;i<s.length();i++){
            ret = ret*26+(s.charAt(i)-'A'+1);
        }
        return ret;
    }
}
```
``` python
class Solution(object):
    def titleToNumber(self, s):
        """
        :type s: str
        :rtype: int
        """
        if len(s)==1:
            return ord(s)-64
        
        return ord(s[-1])-64 + self.titleToNumber(s[:-1]) * 26
```