### Valid Anagram

Given two strings s and t, write a function to determine if t is an anagram of s.

```
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.
```
* 给定两个字符串，写一个函数来确定t是否是s颠倒字母顺序后构成的字符串
``` java
public class Solution {
    public boolean isAnagram(String s, String t) {
        int[] nums = new int[26];
        for(int i=0;i<s.length();i++) nums[s.charAt(i)-'a']++;
        for(int i=0;i<t.length();i++) nums[t.charAt(i)-'a']--;
        for(int n:nums) if(n!=0) return false;
        return true;
    }
}
```
``` python
class Solution(object):
    def isAnagram(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        s, t = list(s), list(t)
        s.sort()
        t.sort()
        if s==t:
            return True
        else:
            return False
            # return sorted(s) == sorted(t)
```
* 利用Hashtable求解
``` python
class Solution(object):
    s1, t1 = {}, {}
    for i in s:
        s1[i] = s1.get(i, 0)+1
    for i in t:
        t1[i] = t1.get(i, 0)+1
    return s1==t1
```