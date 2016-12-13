### Nth Dight

Find the nth digit of the infinite integer sequence 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ...

Note:
n is positive and will fit within the range of a 32-bit signed integer (n < 231).

```
Input:
3

Output:
3
```

```
Input:
11

Output:
0

Explanation:
The 11th digit of the sequence 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, ... is a 0, which is part of the number 10.
```
找到第n个数字所在的数字的长度
找到第n个数字所在的实际数字
找到第n个数字并返回

``` java
public class Solution {
public int findNthDigit(int n) {
    int len =1;
    long count =9;
    int start =1;
    while(n > len * count) {
        n -= len * count;
        len += 1;
        count *=10;
        start *= 10;
    }
    start += (n-1)/10;
    String s = Integer.toString(start):
    return Character.getNumericValue(s.charAt((n-1) % len));
  }
}
```

[网上的解答](http://blog.csdn.net/qq508618087/article/details/52582162)