### Intersection of Two Arrays

Given two arrays, write a function to compute their intersection.

* 返回之间单位交集

```
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2].
```
``` java
public class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        HashSet<Integer> set = new HashSet<>();
        HashSet<Integer> res = new HashSet<>();
        for(int i=0;i<nums1.length;i++){
            set.add(nums1[i]);
        }
        for(int i=0;i<nums2.length;i++){
            if(set.contains(nums2[i])){
                res.add(nums2[i]);
             }
         }
         int[] result = new int[res.size()];
         int i=0;
         for(Integer s: res){
              result[i++] = s;
          }
         return result;
        }
 }
```
* 排序后，设置两个指针，如果相等，则存入HashSet中，否则后移
``` java
public class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        HashSet<Integer> set = new HashSet<>();
        Arrays.sort(nums1);
        Arrays.sort(nums2);
        int i=0;
        int j=0;
        while(i<nums1.length && j<nums2.length){
            if(nums1[i]<nums2[j]){
                i++;
            }else if(nums1[i]>nums2[j]){
                j++;
            }else{
                set.add(nums1[i]);
                i++;
                j++;
            }
        }
        int[] result = new int[set.size()];
        int n=0;
        for(Integer num:set){
            result[n++]=num;
        }
        return result;
    }
}
```
* 下面是利用Java8的流操作
``` java
public class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Set<Integer> set = Arrays.stream(nums1).boxed().collect(Collectors.toSet());
        return Arrays.stream(nums2).distinct().filter(e->set.contains(e)).toArray();
    }
}
```

``` python
class Solution(object):
    def intersection(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        return list(set(nums1) & set(nums2))
        
```
``` python
class Solution(object):
    def intersection(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        res = []
        for n1 in nums1:
            if n1 in nums2 and n1 not in res:
                res.append(n1)
        return res
```