### Roman to Integer

Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

* 给定一个罗马数子，将其转化为Integer
```
* 相同的数字连写，所表示的数等于这些数字相加得到的数，如 Ⅲ=3；
* 小的数字在大的数字的右边，所表示的数等于这些数字相加得到的数，如 Ⅷ=8、Ⅻ=12；
* 小的数字（限于 Ⅰ、X 和 C）在大的数字的左边，所表示的数等于大数减小数得到的数，如 Ⅳ=4、Ⅸ=9；
* 在一个数的上面画一条横线，表示这个数增值 1,000 倍，如

```
``` java
public class Solution {
    public int romanToInt(String s) {
        Map<Character, Integer> map = new HashMap<>();
        map.put('I', 1);
        map.put('V', 5);
        map.put('X', 10);
        map.put('L', 50);
        map.put('C',100);
        map.put('D', 500);
        map.put('M', 1000);
        
        int sum =0;
        char pre='!';
        for(int i=s.length()-1;i>=0;i--){
            char str = s.charAt(i);
            int temp = map.get(str);
            if(temp<sum && pre !=str) sum-=temp;
            else sum+=temp;
            
            pre = str;
        }
        return sum;
    }
}
```

``` java
public class Solution {
    public int romanToInt(String s) {
        int ret = 0;
        for(int i=s.length()-1;i>=0;i--){
            char str = s.charAt(i);
            switch(str){
                case 'I':
                    ret += (ret>=5 ? -1:1);
                    break;
                case 'V':
                    ret+=5;
                    break;
                case 'X':
                    ret +=10*(ret>=50 ? -1 :1);
                    break;
                case 'L':
                    ret+=50;
                    break;
                case 'C':
                    ret+=100*(ret>=500 ? -1 :1);
                    break;
                case 'D':
                    ret+=500;
                    break;
                case 'M':
                    ret+=1000;
                    break;
                    
            }
        }
        return ret;
    }
}
```
``` python
class Solution(object):
    def romanToInt(self, s):
        """
        :type s: str
        :rtype: int
        """
        d = {'M':1000, 'D':500, 'C':100, 'L':50, 'X':10, 'V':5, 'I':1}
        ret, p = 0, 'I'
        for temp in s[::-1]:
            ret, p = ret-d[temp] if d[temp]<d[p] else ret+d[temp], temp
        return ret
        
```