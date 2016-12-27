### Subsets

Given a set of distinct integers, nums, return all possible subsets.Note: The solution set must not contain duplicate subsets.

* 给定一组不重复的整数，返回所有可能的子集，必须返回不重复的子集

```
If nums = [1,2,3], a solution is:

[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```
``` java
public class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        //Arrays.sort(nums);
        List<List<Integer>> ret = new ArrayList<>();
        help(ret, new ArrayList<>(), nums, 0);
        return ret;
    }
    public void help(List<List<Integer>> ret, List<Integer> temp, int[] nums, int start) {
        ret.add(new ArrayList<>(temp));
        for(int i=start;i<nums.length;i++) {
            temp.add(nums[i]);
            help(ret, temp, nums, i+1);
            temp.remove(temp.size()-1);
        }
    }
}
```

``` java
public class Solution {
    public List<List<Integer>> subsrts(int[] nums) {
        List<List<Integer>> ret = new ArrayList<>();
        ret.add(new ArrayList<>());
        //Arrays.sort();
        for(int n: nums) {
            List<List<Integer>> new_ret = new ArrayList<>();
            for(List<Integer> list : ret) {
                List<Integer> temp = new ArrayList<>(list);
                temp.add(n);
                new_ret.add(temp);
            }
            ret.addAll(new_ret);
         }
         return ret;
      }
}
```