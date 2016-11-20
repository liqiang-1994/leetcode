### Isomorphic Strings
Given two strings s and t, determine if they are isomorphic.

Two strings are isomorphic if the characters in s can be replaced to get t.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.

* 给定两个字符串s和t，确定它们是否是同构的。如果s中的字符可以替换为t，则两个字符串是同构的。

``` 
"egg", "add"  -->return true
"foo" , "bar"   --> return false
"paper", "title"  --> return true
```
``` java
public class Solution {
   public boolean isIsomorphic(String s, String t) {
      HashMap map1 = new HashMap();
      HashMap map2 = new HashMap();
      if(s.length() != t.length()) return false;
      for(Integer i=0;i< s.length(); i++) {
         if(map1.put(s.charAt(i), i) != map2.put(t.charAt(i), i)) {
             return false;
           }
        }
        return true;
     }
 }
         
```

``` python
class Solution(object):
    def isIsomorphic(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        return len(set(zip(s,t))) == len(set(s)) == len(set(t))
        return len(set(s)) == len(set(zip(s, t))) == len(set(t))#比上面的写法更快
```