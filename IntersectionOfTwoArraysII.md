### Intersection of Two Arrays II

Given two arrays, write a function to compute their intersection.

* 计算两个数组的交集，结果中每个元素应显示为在两个数组中显示的次数

```
Given nums1 = [1, 2, 2, 1], nums2 = [2, 2], return [2, 2].
```
``` java
public class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        HashMap<Integer,Integer> map = new HashMap<>();
        ArrayList<Integer> list = new ArrayList<>();
        
        for(int i=0;i<nums1.length;i++){
            if(map.containsKey(nums1[i])) map.put(nums1[i], map.get(nums1[i])+1);
            else map.put(nums1[i], 1);
        }
        
        for(int i=0;i<nums2.length;i++){
            if(map.containsKey(nums2[i]) && map.get(nums2[i])>0){
                list.add(nums2[i]);
                map.put(nums2[i], map.get(nums2[i])-1);
            }
        }
        int[] res = new int[list.size()];
        int k=0;
        for(Integer n:list){
            res[k++]=n;
        }
        return res;
    }
}
```
``` java
public class Solution {
    public int[] intersect(int[] nums1, int[] nums2) {
        ArrayList<Integer> list = new ArrayList<>();
        Arrays.sort(nums1);
        Arrays.sort(nums2);
        int i=0;
        int j=0;
        while(i < nums1.length && j < nums2.length){
            if(nums1[i]<nums2[j]){
                i++;
            }else if(nums1[i]>nums2[j]){
                j++;
            }else{
                list.add(nums2[j]);
                i++;
                j++;
            }
        }
        int[] res = new int[list.size()];
        int k=0;
        for(Integer n:list){
            res[k++]=n;
        }
        return res;
    }
}
```
``` python
class Solution(object):
    def intersect(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        temp, res = {}, []
        for n1 in nums1:
            temp[n1] = temp.get(n1, 0)+1
        for n2 in nums2:
            if n2 in temp and temp[n2] >0:
                res.append(n2)
                temp[n2]-=1
        return res
```
``` python
from collections import Counter

class Solution(object):
    def intersect(self, nums1, nums2):
        c1, c2 = Counter(nums1), Counter(nums2)
        return sum([[num] * min(c1[num], c2[num]) for num in c1 & c2], [])

```