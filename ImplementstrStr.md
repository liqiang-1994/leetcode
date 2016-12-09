### implement strStr()

Implement strStr().

Returns the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

* 返回needle在haystack中第一次出现的索引，如果needle不是haystack的一部分，返回-1

``` java
public class Solution {
    public int strStr(String haystack, String needle) {
        for(int i=0; ;i++){
            for(int j=0; ;j++){
                if(j==needle.length()) return i;
                if((i+j)==haystack.length()) return -1;
                if(needle.charAt(j)!=haystack.charAt(i+j)) break;
            }
        }
    }
}
```

``` python
class Solution(object):
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        if needle == "":
            return 0
            
        for i in range(len(haystack)-len(needle)+1):
            for j in range(len(needle)):
                if haystack[i+j]!=needle[j]:
                    break
                if j==len(needle)-1:
                    return i
        return -1
```