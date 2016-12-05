### Add Digits

Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.

* 给定一个非负整数，重复相加所有数子，直到结果只有一个数子

``` 
Given num = 38, the process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return it.
```
```
1    1
2    2
3    3
4    4
5    5
6    6
7    7
8    8    
9    9    
10    1
11    2
12    3    
13    4
14    5
15    6
16    7
17    8
18    9
19    1
20    2
```
* 从上可知大于9的树根都是对9取余
```
public class Solution {
    public int addDigits(int num) {
        return (num-1)%9+1;
    }
}
```
``` java
public class Solution {
    public int addDigits(int num) {
        return num==0 ? 0 : (num%9==0 ? 9 : (num%9));
    }
}
```