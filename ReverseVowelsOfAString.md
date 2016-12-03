### Reverse Vowels of a String

Write a function that takes a string as input and reverse only the vowels of a string.

* 写一个函数，接受一个字符串作并且只反转一个字符串的元音。元音包括a,e,i,o,u.
```
Given s = "hello", return "holle".

Given s = "leetcode", return "leotcede".
```
``` java
public class Solution {
    public String reverseVowels(String s) {
        char[] str = s.toCharArray();
        int start = 0;
        int end = s.length()-1;
        String pattern = "aeiouAEIOU";
        while(start < end){
            while(start<end && !pattern.contains(str[start]+"")) start++;
            while(start<end && !pattern.contains(str[end]+"")) end--;
            
            char temp = str[start];
            str[start] = str[end];
            str[end]=temp;
            
            start++;
            end--;
        }
        return new String(str);
    }
}
```

``` python
class Solution(object):
    def reverseVowels(self, s):
        """
        :type s: str
        :rtype: str
        """
        vowels = (c for c in reversed(s) if c in 'aeiouAEIOU')
        return re.sub('(?i)[aeiou]', lambda m: next(vowels), s)
```
[Python 的几种解法](https://discuss.leetcode.com/topic/43463/1-2-lines-python-ruby/2)















