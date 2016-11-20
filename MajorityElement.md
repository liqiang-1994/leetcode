### Majority Element

Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

* 给定一个大小为n的数组，找到多数元素，多数元素是出现超次数过 n/2 倍的元素

``` java
public class Solution {
   public int majorityElement(int[] nums) {
      Arrays.sort(nums);
      return nums[nums.length/2];
   }
}
```
* 下面这个方法是利用HashMap,键是nums的值，值是nums中的数出现的次数，这个方法是对HashMap排序显然效率不高(33ms)，写在这里是对HashMap如何排序
``` java
public class Solution {
   public int majorityElement(int[] nums) {
      HashMap<Integer, Integer> map = new HashMap<>();
      
      for(int n : nums) {
         if(!map.containsKey(n)) {
            map.put(n, 1);
         }else {
            map.put(n, map.get(n) +1);
          }
        }
      Set<Map.Entry<Integer, Integer>> entrySet = map.entrySet();
      List<Map.Entry<Integer, Integer>> list = new LinkedList<>(entrySet);
      Collections.sort(list, new Comparator<Map.Entry<Integer, Integer>>() {
         public int compare(Map.Entry<Integer, Integer> 01, Map.Entry<Integer, Integer> o2) {
            return o1.getValue().compareTo(o2.getValue());
         }
     });
     return list.get(list.size()-1).getKey();
   }
 }   
 //当然也可以不进行排序，如下
 if(map.get(n) >nums.length/2) {
                number = n;
                break;
            }
```
* 使用摩尔投票法，每出现两个不同的元素，则成对删除(或者说抵消)，最终剩下的就是出现次数最多的元素
``` java
public class Solution {
   public int majorityElement(int[] nums) {
      int count=0, rnum =0;
      for(int n : nums) {
         if(count == 0) rnum = n;
         if(rnum != n) count--;
         else count++;
      }
      return rnum;
   }
}
```
* 利用python内建函数，beat 99.31%
``` python
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        nums.sort()
        return nums[len(nums)/2]
```

* python版的投票法
``` python
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        count, rnum =0, 0
        for i in nums:
            if count == 0:
                rnum = i
            if rnum != i:
                count -=1
            else:
                count+=1
            return rnum
```
