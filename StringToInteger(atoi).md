### String to Integer (atoi)

Implement atoi to convert a string to an integer.

* 实现atoi将字符串转化为整数

Requirements for atoi:
The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial plus or minus sign followed by as many numerical digits as possible, and interprets them as a numerical value.

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.

If the first sequence of non-whitespace characters in str is not a valid integral number, or if no such sequence exists because either str is empty or it contains only whitespace characters, no conversion is performed.

If no valid conversion could be performed, a zero value is returned. If the correct value is out of the range of representable values, INT_MAX (2147483647) or INT_MIN (-2147483648) is returned.

* atoi函数要求丢弃所需的空格字符，直到找到第一个非空字符，然后从该字符开始，采用可选的初始加号或减号，后跟尽可能多的数子，并将其解释为数值。如果str中的非空格字符的第一个序列不是有效的整数，或者如果没有这样的序列，因为str是空的或者它只包含空格字符，则不执行转换。如果不能执行有效的转换，则返回零值。如果正确的值超出可表示值的范围，则返回INT_MAX（2147483647）或INT_MIN（-2147483648）。

```
1. null or empty string
2. white spaces
3. +/- sign
4. calculate real value
5. handle min & max
```
``` java
public class Solution {
    public int myAtoi(String str) {
        if(str == null || str.length()<1) return 0;
        String s = str.trim();
        char flag = '+';
        int i=0;
        if(s.charAt(i) =='-') {
            flag = '-';
            i++;
        }else if(s.charAt(i)=='+') {
            i++;
        }
        double ret =0;
        while(s.length()>i && s.charAt(i)>='0' && s.charAt(i) <='9' ){
            ret = ret*10 + (s.charAt(i) - '0');
            i++;
        }
        if(flag =='-') ret = (-ret);
        if(ret > Integer.MAX_VALUE) return Integer.MAX_VALUE;
        if(ret < Integer.MIN_VALUE) return Integer.MIN_VALUE;
        return  (int) ret;
     }
 }
```
``` java
public class Solution {
    public int myAtoi(String str) {
       if(str.isEmpty()) return 0;
       int sign = 1, ret = 0, i=0;
       while(str.charAt(i)==' ') i++;
       if(str.charAt(i)=='-'||str.charAt(i)=='+'){
           sign = str.charAt(i++)=='-' ? -1 : 1;
       }
       while(i<str.length() && str.charAt(i)>='0' && str.charAt(i)<='9'){
           if(ret>Integer.MAX_VALUE/10 || (ret==Integer.MAX_VALUE/10 && str.charAt(i)-'0'>7)){
               return (sign==1) ? Integer.MAX_VALUE : Integer.MIN_VALUE;
           }
           ret = ret*10+(str.charAt(i++)-'0');
       }
       return ret*sign;
    }
}
```
``` c
int myAtoi(char* str) {
    int sign = 1, base = 0, i = 0;
    while (str[i] == ' ') { i++; }
    if (str[i] == '-' || str[i] == '+') {
        sign = 1 - 2 * (str[i++] == '-'); 
    }
    while (str[i] >= '0' && str[i] <= '9') {
        if (base >  INT_MAX / 10 || (base == INT_MAX / 10 && str[i] - '0' > 7)) {
            if (sign == 1) return INT_MAX;
            else return INT_MIN;
        }
        base  = 10 * base + (str[i++] - '0');
    }
    return base * sign;
}
```
* 利用正则求解
``` python
class Solution(object):
    def myAtoi(self, str):
        """
        :type str: str
        :rtype: int
        """
        str = str.strip()
        str = re.findall('(^[\+\-0]*\d+)', str)
        try:
            ret = int(''.join(str))
            MAX_INT = 2147483647
            MIN_INT = -2147483648
            if ret > MAX_INT >0:
                return MAX_INT
            elif ret < MIN_INT <0:
                return MIN_INT
            else:
                return ret
        except:
            return 0
```