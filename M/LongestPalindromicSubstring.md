### Longest Palindromic Substring

Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

* 给定一个字符串，在s中找到最长的回文字符串，可以假设s的最大长度为1000

``` 
Input: "babad"

Output: "bab"

Note: "aba" is also a valid answer.
```
```
Input: "cbbd"

Output: "bb"
```

``` java
public class Solution {
    private int index, maxLen;
    public String longestPalindrome(String s) {
        int len = s.length();
        if(len<2) return s;
        for(int i=0;i<len-1;i++){
            sub(s, i, i); //若为奇数长度
            sub(s, i, i+1);
        }
        return s.substring(index, maxLen+index);
     }
     public void sub(String s, int m, int n) {
         while(m<s.length()  && n>=0 && s.charAt(m)==s.charAt(n)){
             m++;
             n--;
         }
         if(maxLen < m-n-1){
             index = n+1;
             maxLen = m-n-1;
          }
      }
 }
```

``` java
public class Solution {
    public String longestPalindrome(String s) {
        String ret = "";
        int  cur = 0;
        for(int i=0;i<s.length();i++) {
            if(sub(s, i-cur-1,i)) {
                ret = s.substring(i-cur-1, i+1);
                cur = cur+2;
            }else if(sub(s, i-cur, i)) {
                ret = s.substring(i-cur, i+1);
                cur = cur+1;
            }
         }
         return ret;
     }
     public boolean sub(String s, int begin, int end) {
         if(begin<0) return false;
         while(begin<end) {
             if(s.charAt(begin++) != s.charAt(end--)) return false;
          }
          return true;
      }
}      
```