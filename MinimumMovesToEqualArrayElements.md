### MInimum Moves to Equals Array Elements
Given a non-empty integer array of size n, find the minimum number of moves required to make all array elements equal, where a move is incrementing n - 1 elements by 1.

* 给定大小为n的非空整数数组，找到使所有数组元素相等所需的最小移动数，其中移动将n-1个元素递增1

* Example
```
Input:
[1,2,3]

Output:
3

Explanation:
Only three moves are needed (remember each move increments two elements):
* 总共3个数,每个动作只需要对两个元素加1，最后相等截至
[1,2,3]  =>  [2,3,3]  =>  [3,4,3]  =>  [4,4,4]
```
* 思路：设置最小的元素，所有的元素到与最小元素相等所需的步驟，找到数组中最小元素设置为基准值，遍历1到n-1个元素与基准值相减，直到使数组的元素相等
``` java
public class Solution {
    public int minMoves(int nums[]) {
        if(nums.length ==0) return 0;
        int min = nums[0];
        for(int n: nums) {
             min = Math.min(min,n);  //找出最小的数
        }
        int count =0;
        for(int n:nums) {
            count +=n-min;
          }
          return count;
     }
}
```
* 将nums[0]设置为基准值，遍历1到n-1个元素与基准值相减，直到使数组的元素相等
``` java
public class Solution {
    public int minMoves(int[] nums) {
        int count =0;
        int min = nums[0];
        for (int i=0;i<nums.length;i++) {
            if(nums[i] >= min) {
                count +=nums[i]-min;
            }else {
                count +=(min -nums[i])*i;
                min = nums[i];
            }
        }
        return count;
    }
}
```
* 利用列表的便捷性，使用内置函数，相差的数即是移动数
``` python
class Solution(object):
    def minMoves(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        return sum(nums) - len(nums) * min(nums)
```