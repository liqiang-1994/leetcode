### Tow Sum

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution.

给定一个整形数组，如果两个数字值相加等于特定的目标值，即返回两个数组的索引

* 思路：利用HashMap的存储键值对的特性，数据结构即是这样{nums[i], i}，以值为键以索引为值，从i=0到i=length(nums)循环整个数组，如果能找到(target-nums[i])这个键且索引不等于i，就说明找到了
``` text
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
``` java
import java.util.HashMap;

public class test1 {

    public static int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for(int i=0;i<nums.length;i++) {
            map.put(nums[i], i);
        }

        for(int i=0;i<nums.length;i++) {
            if (map.get(target - nums[i])!= null && map.get(target - nums[i]) != i) {
                return new int[]{i, map.get(target - nums[i])};
            }
        }
        return new int[]{0};
    }

    public static void main(String[] args) {
        int[] number = {2, 7, 11, 15};
        int[] number1 = {0, 4, 3, 0};
        int[] q = twoSum(number1, 0);
        for(int i=0;i<q.length;i++) {
            System.out.print(q[i]);
        }
    }
}
```
*  利用python内建的dict(字典)数据结构存储键值对，思路同上就不多说了，
``` python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        indexs = []
        sums = {}
        for i in range(len(nums)):
            sums[nums[i]] = i

        for i in range(len(nums)):
            if(sums.get(target - nums[i]) != i and (target-nums[i]) in sums):
                indexs.append(i)
                indexs.append(sums.get(target-nums[i]))
                return indexs
        return []

```