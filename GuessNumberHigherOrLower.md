### Guess Number Higher or Lower

We are playing the Guess Game. The game is as follows:I pick a number from 1 to n. You have to guess which number I picked.Every time you guess wrong, I'll tell you whether the number is higher or lower.

You call a pre-defined API guess(int num) which returns 3 possible results (-1, 1, or 0):

* 一个猜数子游戏，选择一个从1到n的游戏，每次如果猜错了，告诉我正确的数字是高还是低

您调用预定义的API猜测（int num），返回3个可能的结果（-1,1或0）

``` java
/* The guess API is defined in the parent class GuessGame.
   @param num, your guess
   @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
      int guess(int num); */
public class Solution {
    public int guessNumber(int n) {
        int low =1, high =n;
        while(low < high) {
            int mid = low +(high-low)/2;
            int g = guess(mid);
            if (g==1) low =mid+1;
            else if(g==-1) high = mid -1;
            else return mid;
        }
        return low;
    }
}
```
``` python

class Solution(object):
    def guessNumber(self, n):
        """
        :type n: int
        :rtype: int
        """
        low, high = 1, n
        while low < high:
            mid = (low+high)/2
            low, high  = ((mid, mid), (mid+1, high), (low, mid-1))[guess(mid)]
        return low
```