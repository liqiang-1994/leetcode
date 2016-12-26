### Subsets II

Given a collection of integers that might contain duplicates, nums, return all possible subsets.Note: The solution set must not contain duplicate subsets.

* 给定可能包含重复的nums的整数集合，返回所有可能的子集(结果不能包含重复的子集)

```
If nums = [1,2,2], a solution is:

[
  [2],
  [1],
  [1,2,2],
  [2,2],
  [1,2],
  []
]
```

``` java
public class Solution {
    public List<List<Integer>> subsetsWithDup(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> ret = new ArrayList<>();
        ret.add(new ArrayList<>());
        int size=0,start=0;
        for(int i=0;i<nums.length;i++){
            start=(i>=1 && nums[i]==nums[i-1]) ? size :0;
            size=ret.size();
            for(int j=start;j<size;j++){
                ArrayList<Integer> temp=new ArrayList<>(ret.get(j));
                temp.add(nums[i]);
                ret.add(temp);
            }
        }
        return ret;
    }
}
```

