### Count and Say

The count-and-say sequence is the sequence of integers beginning as follows:Given an integer n, generate the nth sequence.

* 计数和说出序列是整数序列,给定一个Integer，输出第n个序列

``` 
1, 11, 21, 1211, 111221, ...

1 is read off as "one 1" or 11.
11 is read off as "two 1s" or 21.
21 is read off as "one 2, then one 1" or 1211.
```

``` java
public class Solution {
    public String countAndSay(int n) {
        if(n<=0) return "";
        String result="1";
        int i=1;
        while(i<n){
            StringBuilder sb = new StringBuilder();
            int count=1;
            for(int j=1;j<result.length();j++){
                if(result.charAt(j)==result.charAt(j-1)){
                    count++;
                }else{
                    sb.append(count);
                    sb.append(result.charAt(j-1));
                    count=1;
                }
            }
            sb.append(count);
            sb.append(result.charAt(result.length()-1));
            result = sb.toString();
            i++;
        }
        return result;
    }
}
```
``` python
class Solution(object):
    def countAndSay(self, n):
        """
        :type n: int
        :rtype: str
        """
        s="1"
        for w in range(n-1):
            s=''.join(str(len(list(group)))+ digit for digit,group in itertools.groupby(s))
        return s
```