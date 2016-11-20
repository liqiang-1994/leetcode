### Word Pattern
Given a pattern and a string str, find if str follows the same pattern.

Here follow means a full match, such that there is a bijection between a letter in pattern and a non-empty word in str.

* 给定模式和字符串str，使得在模式中的字母和str中的非空字之间存在映射

``` 
pattern =“abba”，str =“dog cat cat dog”应该返回true。
pattern =“abba”，str =“dog cat cat fish”应该返回false。
pattern =“aaaa”，str =“dog cat cat dog”应该返回false。
pattern =“abba”，str =“dog dog dog dog”应该返回false。
假定pattern只包含小写字母，str包含由单个空格分隔的小写字母
```
* 使用HashMap建立映射关系，利用HashMap如果存入键相等，则会更新值，依此建立唯一映射
``` java
public class Solution {
   public boolean wordPattern(String pattern, String str) {
      HashMap map = new HashMap();
      String[] strs = str.split(" ");
      if(pattern.length() != strs.length) return false;
      for(Integer i=0;i<strs.length;i++) { //HashMap不能使用基本数据类型
         if(map.put(pattern.charAt(i), i) != map.put(strs[i], i)) {
            return false; 
         }
      }
      return true;
   }
}
          
```

``` python
class Solution(object):
    def wordPattern(self, pattern, str):
        """
        :type pattern: str
        :type str:str
        :rtype:bool
        """
        strs = str.split(' ')
        if len(pattern) != len(strs):
            return False
        s =set(zip(pattern, strs))
        return len(s) == len(set(pattern)) == len(set(strs))
```
``` python
class Solution(object):
    def wordPattern(self, pattern, str):
        """
        :type pattern: str
        :type str: str
        :rtype: bool
        """
        strs = str.split(' ')
        return len(set(zip(pattern, strs))) == len(set(strs)) == len(set(pattern)) and len(pattern) == len(strs)
```
