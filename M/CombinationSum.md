### 

Given a set of candidate numbers (C) (without duplicates) and a target number (T), find all unique combinations in C where the candidate numbers sums to T.

The same repeated number may be chosen from C unlimited number of times.

 * 给定一组侯选数字(C)(没有重复)和目标数字(T)，找到C中所有唯一组合使其其中侯选数总和为T
 
```
 For example, given candidate set [2, 3, 6, 7] and target 7, 
A solution set is: 

[
  [7],
  [2, 2, 3]
]
```

``` java
public class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target){
        List<List<Integer>> ret = new ArrayList<>();
        Arrays.sort(candidates);
        combination(ret, new ArrayList<>(), candidates, target, 0);
        return ret;
    }
    public void combination(List<List<Integer>> ret, List<Integer> temp, int[] nums, int target, int start) {
        if(target<0) return;
        else if(target==0) ret.add(new ArrayList<>(temp));
        else{
            for(int i=start;i<nums.length;i++) {
                temp.add(nums[i]);
                combination(ret, temp, nums, target-nums[i], i);
                temp.remove(temp.size()-1);
            }
        }
    }
}
```
public class Solution {
    public List<List<Integer>> combinationSum(int[] candidates, int target) {
        List<List<Integer>> ret = new ArrayList<>();
        Arrays.sort(candidates);
        combination(ret, new ArrayList<>(), candidates, target, 0);
        return ret;
    }
    public void combination(List<List<Integer>> ret, List<Integer> temp, int[] nums, int target, int start){
        if(target<0) return;
        else if(target==0) ret.add(new ArrayList<>(temp));
        else{
            for(int i=start;i<nums.length;i++){
                temp.add(nums[i]);
                combination(ret, temp, nums,target-nums[i],i);
                temp.remove(temp.size()-1);
            }
        }
    }
}