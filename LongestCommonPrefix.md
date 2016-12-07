### Longest Common Prefix

Write a function to find the longest common prefix string amongst an array of strings.

* 返回一个字符串数组中的最长的公共前缀字符串

``` java
public class Solution {
    public String longestCommonPrefix(String[] strs) {
        if(strs==null || strs.length==0) return "";
        int i=0;
        String pre = strs[0];
        while(i<strs.length){
            while(strs[i].indexOf(pre)!=0){
                pre =pre.substring(0, pre.length()-1);
            }
            i++;
        }
        return pre;
    }
}
```

``` python
class Solution(object):
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        if not strs:
            return ""
        for i, temp in enumerate(zip(*strs)):
            if len(set(temp))>1:
                return strs[0][:-i]
        else:
            return min(strs)
```