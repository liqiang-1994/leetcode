### Excel Sheet Column Title

Given a positive integer, return its corresponding column title as appear in an Excel sheet.

```
    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
```
* 本质是一个将10进制转化为26进制的数，由于下标从1开始而不是从0开始，因此要减一

``` java
public class Solution {
    public String convertToTitile(int n) {
        String ret ="";
        while(n>0){
            ret = (char)((n-1)%26+'A')+ret;
            n=(n-1)/26;
        }
        return ret;
     }
}
```
``` java
public class Solution {
    public String convertToTitle(int n) {
        return n==0 ? "" : convertToTitle((n-1)/26)+(char)((n-1)%26 + 'A');
    }
}
```
``` python
class Solution(object):
    def convertToTitle(self, n):
        """
        :type n: int
        :rtype: str
        """
        temp =[chr(x) for x in range(ord('A'), ord('Z')+1)]
        ret = []
        while n >0:
            ret.append(temp[(n-1)%26])
            n=(n-1)//26
        ret.reverse()
        return ''.join(ret)
```