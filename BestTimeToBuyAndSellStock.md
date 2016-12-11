### Best Time to Buy and Sell Stock

Say you have an array for which the ith element is the price of a given stock on day i.If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

* 假设你有一个数组，其中第i个元素是第i天给定的股票价格，如果只被允许完成最多一个交易(即买一个并卖出一个股票)

``` 
Input: [7, 1, 5, 3, 6, 4]
Output: 5

max. difference = 6-1 = 5 (not 7-1 = 6, as selling price needs to be larger than buying price)
```

```
Input: [7, 6, 4, 3, 1]
Output: 0

In this case, no transaction is done, i.e. max profit = 0.
```
* 卖出的价格必须大于卖入的价格

``` java
public class Solution {
     public int maxProfit(int[] prices) {
         if(prices.length==0) return 0;
         int result = 0;
         int low = prices[0];
         for(int i=0;i<prices.length;i++) {
             if(prices[i]<low) low=prices[i];
             if((prices[i]-low)>result) result = prices[i]-low;
         }
         return result;
     }
}
```

``` python
class Solution(object):
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        maxCur, maxSoFar = 0, 0
        for i in range(1, len(prices)):
            x=prices[i] - prices[i-1]
            maxCur +=x
            maxCur = max(0, maxCur)
            maxSoFar = max(maxCur, maxSoFar)
        return maxSoFar
```

[最大子数列求和](https://zh.wikipedia.org/wiki/最大子数列问题)