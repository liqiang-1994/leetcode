### Nim Game

You are playing the following Nim Game with your friend: There is a heap of stones on the table, each time one of you take turns to remove 1 to 3 stones. The one who removes the last stone will be the winner. You will take the first turn to remove the stones.

Both of you are very clever and have optimal strategies for the game. Write a function to determine whether you can win the game given the number of stones in the heap.

For example, if there are 4 stones in the heap, then you will never win the game: no matter 1, 2, or 3 stones you remove, the last stone will always be removed by your friend.

* 
你和你的朋友一起玩下面的Nim游戏：在桌子上有一堆石头，每次你轮流去掉1到3块石头。 去除最后一块石头的人将是赢家。 你会采取第一个回合去除石头。编写一个函数来确定是否可以赢得游戏给定的堆数的石头。例如，如果堆中有4块石头，那么你永远不会赢得比赛：无论你删除1，2或3块石头，最后的石头将永远被你的朋友删除。
* 显然如果是4的倍数，如4，8，12... 都不会赢的
``` java
public class Solution {
   public boolean canWinNim(int n) {
      if(n%4==0) return false;
      else return true;
      // or return !(n%4==0);
      // or return (n%4==0) ? false : true;
   }
 }
```

