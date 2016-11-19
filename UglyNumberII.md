### Ugly Number II
Write a program to find the n-th ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5. For example, 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 is the sequence of the first 10 ugly numbers.

Note that 1 is typically treated as an ugly number.

* 求出第n个Ugly Number(素因子只有2，3，5的正数)

* 声明三个表示2，3，5的乘数数组列表中的相应索引a,b,c,由于每个前面的丑数乘以一个乘以一个乘数将产生一个新的丑数，从起始索引0开始，并将每个乘数乘以该索引处的丑数，得到最小的乘积，它是三个中的下一个丑数，相应的乘数索引将递增1，如此递归下去
``` java
public class Solution {
   public int nthUglyBumber(int n) {
      if(n <= 0) return 0;
      int a=0, b=0, c=0;
      List<Integer> list = new ArrayList<>();
      list.add(1);  //将1这个Ugly Number存入
      while(list.size() < n) {
         int next = Math.min(list.get(a)*2, Math.min(list.get(b)*3, list.get(c)*5));
         if(list.get(a)*2 == next) a++;
         if(list.get(b)*3 == next) b++;
         if(list.get(c)*5 == next) c++;
      }
     return list.get(list.size()-1);
     }
 }
```
* 下面的方法原理同上，只不过使用数组代替ArrayList,使用更多的静态变量而不是局部变量，only 2ms

``` java
public class Solution {
   static int[] list = new int[3000];
   static boolean flag = false;
   public int nthUglyNumber(int n) {
       if(!falge) {
          flag = true;
          init();
       }
       return list[n-1];
    }
    public static void init() {
       int a=0,b=0, c=0;
       list[0] =1;
       for(int i=0; i<3000;i++) {
          int next = Math.min(list[a]*2, Math.min(list[b]*3, list[c]*5));
          if(list[a]*2 == next) {
             list[i] =next;
             a++;
          }
          if(list[b]*3 == next) {
             list[i] = next;
             b++;
          }
          if(list[c]*5 == next) {
             list[i] = next;
             c++;
          }
        }
    }
} 
```
* 使用元组好像比列表快
``` java
class Solution(object):
    def nthUglyNumber(self, n):
        """
        :type n: int
        :type: int
        """
        l = [1]
        a, b,c =0,0,0
        while n>0:
            n1, n2, n3 = l[a]*2, l[b]*3, l[c]*5
            next = min((n1, n2. n3))
            if n1 == next:
                a+=1
            if n2 == next:
                b+=1
            if n3 == next:
                c+=1
            l.append((next))
            n-=1
        return l[-1]
        
```