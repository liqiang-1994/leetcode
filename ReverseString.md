### Reverse String

Write a function that takes a string as input and returns the string reversed.

* 字符串反转
``` 
Given s = "hello", return "olleh".
```

``` java
public class Solution {
    public String reverseString(String s) {
        char[] str = s.toCharArray();
        int len = str.length;
        for(int i=0;i<len/2;i++) {
            char temp = str[i];
            str[i] = str[len-i-1];
            str[len-i-1] = temp;
        }
        return new String(str);
     }
}
```
``` python
class Solution(object):
    def reverseString(self, s):
        """
        :type s: str
        :rtype: str
        """
        return s[::-1]
        
```