### Valid Palindrome

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

* 给定一个字符串，确定它是否是一个回文串，只考虑字母数子字符
```
"A man, a plan, a canal: Panama" ->return true
"race a car" ->return false
```
``` java
public class Solution {
    public boolean isPalindrome(String s) {
        char[] lists = new char[s.length()];
        int count = 0;
        for(int i=0;i<s.length();i++){
            char c = s.charAt(i);
            if(c>='A'&& c<='Z'){
                lists[count++]=(char)(c+32);
            }else if((c>='a'&& c<='z')||(c>='0'&&c<='9')){
                lists[count++]=c;
            }
        }
        for(int i=0;i<count/2;i++){
            if(lists[i] != lists[count-i-1]){
                return false;
            }
        }
        return true;
    }
}
```
``` python
import re
class Solution(object):
    def isPalindrome(self, s):
        """
        :type s:str
        :rtype: bool
        """
        s =re.sub(r"[^A-Za-z0-9]", '', s).lower()
        if s==s[::-1]:
            return True
        else:
            return False
```