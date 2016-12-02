### Repeated Substring Pattern

Given a non-empty string check if it can be constructed by taking a substring of it and appending multiple copies of the substring together. You may assume the given string consists of lowercase English letters only and its length will not exceed 10000.

* 给定一个非空字符串检查，如果它可以通过取子字符串并将子字符串的多个副本附加在一起构造，可以假定给定的字符串全由小写字母组成，长度不超过10000

```
Input: "abab"

Output: True

Explanation: It's the substring "ab" twice.

Input: "abab"

Output: True

Explanation: It's the substring "ab" twice.

Input: "abcabcabcabc"

Output: True

Explanation: It's the substring "abc" four times. (And the substring "abcabc" twice.)
```
``` java
public class Solution {
    public boolean repeatedSubstringPattern(String str) {
         int len = str.length();
         for(int i=len/2;i>=1;i--){
             if(len%i==0){
                 int num = len/i;
                 String subs = str.substring(0, i);
                 StringBuilder build= new StringBuilder();
                 for(int n=0;n<num;n++){
                     build.append(subs);
                  }
                  if(build.toString().equals(str)) return true;
               }
          }
          return false;
      }
}
```
``` python
class Solution(object):
    def repeatedSubstringPattern(self, str):
        """
        :type str: str
        :rtype: bool
        """
        l = len(str)
        return any(l/d * str[:d] ==str for d in range(1, l) if l%d==0)
```
``` python
class Solution(object):
    def repeatedSubstringPattern(self, str):
        """
        :type str: str
        :rtype: bool
        """
        ss = (str*2)[1:-1]
        return str in ss
```




















