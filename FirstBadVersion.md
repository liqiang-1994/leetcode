### First Bad Version
You are a product manager and currently leading a team to develop a new product. Unfortunately, the latest version of your product fails the quality check. Since each version is developed based on the previous version, all the versions after a bad version are also bad.

Suppose you have n versions [1, 2, ..., n] and you want to find out the first bad one, which causes all the following ones to be bad.

You are given an API bool isBadVersion(version) which will return whether version is bad. Implement a function to find the first bad version. You should minimize the number of calls to the API.

您是产品经理，目前领导一个团队开发新产品。 很抱歉，您的产品的最新版本未通过质量检查。 由于每个版本是基于以前的版本开发的，所有版本在坏版本后也是坏的。

假设你有n个版本[1，2，...，n]，你想找出第一个坏的，这导致所有以下的坏。

你得到一个API bool isBadVersion（version），它将返回版本是否是坏的。 实现一个函数来找到第一个坏版本。 您应该尽量减少对API的调用次数。

* 使用二分法求得第一个错误版本

``` java
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); */
public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
         int start = 1;
         int end = n;
         while(start < end) {
             int mid = start + (end - start)/2; 
             //use it  not mid = (end -start) /2是避免溢出，或者int mid = (end +start) >>>1; 使用无符号移
             if(!isBadVersion(mid)) {
                start = mid+1;
             }else {
                 end = mid;
              }
            }
            return start;
       }
 }
``` 

``` java
public class Solution {
   public int firstBadVersion(int n) {
       return binarySearch(1, n);
     }
     public int binarySearch(int start, int end) {
         long startLong  = start;
         long endLong  = end;
         Long middleLong = (startLong + endLong ) / 2;
         int middle = middleLong.intValue();
         if(isBadVersion(middle)) {
              if(!isBadVersion(middle-1)) {
                return middle;
                }
                return binarySearch(start, middle);
         }else {
              if(isBadVersion(middle +1)) {
                return middle +1;
              }
                return binarySearch(middle+1, end);
             }
        }
 }
```
* 第一种算法的python版
``` python
# The isBadVersion API is already defined for you.
# @param version, an integer
# @return a bool
# def isBadVersion(version):
class Solution(object):
    def firstBadVersion(self, n):
        """
        :type n:int
        :rtype: int
        """
        start =1
        end =n
        while start < end:
            mid = (start + end) >>1
            if not isBadVersion(mid):
                start = mid + 1
            else:
                end = mid
        return start    
```