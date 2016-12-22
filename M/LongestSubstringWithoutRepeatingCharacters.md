### Longest Substring Without Repeating Characters

Given a string, find the length of the longest substring without repeating characters.

* 找出不重复的子字符串的最大长度

```
Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```
* 使用HashMap
``` java
public class Solution {
    public int lengthOfLongestSubstring(String s) {
        if(s.length()==0) return 0;
        HashMap<Character, Integer> map = new HashMap<>();
        int max = 0;
        for(int i=0,j=0;i<s.length(); i++){
            if(map.containsKey(s.charAt(i))){
                j = Math.max(j, map.get(s.charAt(i))+1);
            }
            map.put(s.charAt(i), i);
            max = Math.max(max, i-j+1);
        }
        return max;
     }
}
```
* 使用HashSet
``` java
public class Solution {
    public int lengthOfLongestSubstring(String s){
    if(s.length()==0) return 0;
    int i=0, j=0, max=0;
    while(i<s.length()) {
        if(!set.contains(s.charAt(i))){
            set.add(s.charAt(i++));
            max = Math.max(max, set.size());
         }else{
         set.remove(s.charAt(j++));
         }
      }
      return max;
   }
}
```