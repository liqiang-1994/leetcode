### Permutations II

Given a collection of numbers that might contain duplicates, return all possible unique permutations.

* 给定可能重复的数字集合，返回所有可能唯一的排列

```
[1,1,2] have the following unique permutations:
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
```
``` java
public class Solution {
    public List<List<Integer>> permuteUnique(int[] nums) {
        LinkedList<List<Integer>> rets = new LinkedList<>();
        rets.add(new ArrayList<Integer>());
        for(int i=0;i<nums.length;i++) {
            Set<String> set = new HashSet<>();
            while(rets.peekFirst().size() == i){
                List<Integer> list = rets.removeFirst();
                for(int j=0;j<list.size()+1;j++){
                    List<Integer> temp = new ArrayList<>(list);
                    temp.add(j, nums[i]);
                    if(set.add(temp.toString())) rets.add(temp);
                }
           }
       }
       return rets;
   }
}
```

``` python
class Solution(object):
    def permuteUnique(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        ret = [[]]
        for n in nums:
            new_ret = []
            for temp in ret:
            for i in range(len(temp)+1):
                new_ret.append(temp[:i]+[n]+temp[i:])
                if i < len(temp) and temp[i]==n:break
            ret = new_ret
        return ret
```