### First Unique Character in a String

Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.

* 找出一个字符串中第一个没有重复字符并返回它的索引，否则返回-1

``` 
s = "leetcode"
return 0.

s = "loveleetcode",
return 2.
```

``` java
public class Solution { 
    public int firstUniqChar(String s) {
        int[]  arr = new int[26];
        for(int i=0;i<s.length();i++){
            arr[s.charAt(i)-'a']++;
        }
        for(int i=0;i<s.length();i++){
            if(arr[s.charAt(i)-'a']==1) return i;
        }
        return -1;
     }
 }
```

``` python
class Solution(object):
    def firstUniqChar(self, s):
        """
        :type s: str
        :rtype: int
        """
        return min([s.find(c) for c in string.ascii_lowercase if s.count(c)==1] or [-1])
```

``` python
class Solution(object):
    def firstUniqChar(self, s):
        """
        :type s: str
        :rtype: int
        """
        return min([s.find(k) for k,v in collections.Counter(s).iteritems() if v==1] or [-1])
```