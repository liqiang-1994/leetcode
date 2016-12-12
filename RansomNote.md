### Ransom Note

Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

* 给定一个任意的ransom字符串和一个magazine字符串，编写一个函数，如果可以从magazine构建ransom字符串，则该函数返回true，否则返回false

magazine字符串中的每个字母只能在ransom中使用一次

```
canConstruct("a", "b") -> false
canConstruct("aa", "ab") -> false
canConstruct("aa", "aab") -> true
```

``` java
public class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        int[] arr = new int[26];
        for(char c : magazine.toCharArray()){
            arr[c-'a']++;
        }
        for(char w : ransomNote.toCharArray()){
            if(--arr[w-'a'] < 0) return false;
        }
        return true;
    }
}
```

``` python
class Solution(object):
    def canConstruct(self, ransomNote, magazine):
        """
        :type ransomNote: str
        :type magazine: str
        :rtype: bool
        """
        return not collections.Counter(ransomNote) - collections.Counter(magazine)
        //使用Counter函数将其转化为字典，如果ransomNote减去magazine为空则返回true
```
* 下面是使用Java8的匿名函数和compute()函数的写法
``` java
public class Solution {
    public boolean canConstruct(String ransomNote, String magazine){
        Map<Character, Integer> map = new HashMap<>();
        for(char c : magazine.toCharArray()){
            map.compute(c, (k, v)-> v==null ? 1 : v+1);
        }
        for(char w : ransomNote.toCharArray()){
            if(map.compute(w, (k, v)-> v==null ? -1 : v-1)<0){
                return false;
            }
        }
        return true;
    }
} 
```