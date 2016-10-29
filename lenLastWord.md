### Length of Last Word
Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.

If the last word does not exist, return 0.

Note: A word is defined as a character sequence consists of non-space characters only.

For example, 
Given s = "Hello World",
return 5

*  给定一个由大小写子母和空格组成的字符串，返回最后一个字符串的长度，如果最后一个字不存在返回0

``` java
public class Solution {
    public int lengthOfLastWord(String s) {
         if(s =="" || s==" ")
              return 0;
          else{
                String[] str = s.trim().split(" ");
                 return str[str.length - 1].length();
          }
     }
}
```
``` java
public class Solution {
  public int lengthOfLastWord(String s) {
        return s.trim().length() - s.trim().lastIndexOf(" ")-1;
```
``` java
public class Solution {
    public int lengthOfLastWord(String s) {
        if(s==null) return 0;
        int count =0;
        String ss=s.trim();
        for(int i=ss.length()-1;i>=0;i--){
            if(ss.charAt(i)!= ' '){
                count++;
            }else{
                break;
            }
        }
        return count;
    
    }
}
```
* 使用Matcher类的正则匹配
``` java
public class Solution {
    public int lengthOfLastWord(String s) {
        if(s.length() == 0 || s.matches(" *"))
          return 0;
        String [] ans = s.split(" ");
        return ans[ans.length-1].length();  
    }
}
```
``` java
public class Solution {
public int lengthOfLastWord(String s) {
     if(s == null) return 0;
    int wordLen = 0;
    for(int i = s.length() - 1; i>= 0; i--){
        if(s.charAt(i) != ' '){
            wordLen++;
        }else if(wordLen > 0){
            break;
        }
    }
    return wordLen;
 }
}
``` 
``` python
class Solution(object):
    def lengthOfLastWord(self, s):
        """
        :type s: str
        :rtype: int
        """
        return len(s.strip().split(" ")[-1])
```