### 3Sum

Given an array S of n integers, are there elements a, b, c in S such that a + b + c = 0? Find all unique triplets in the array which gives the sum of zero.

* 给定n个整数数组S，在S中存在元素a, b, c，使得a+b+c=0找到数组中唯一的三元组

```
For example, given array S = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

``` java
public class Solution {
    List<List<Integer>> ret = new ArrayList<>();
    public List<List<Integer>> threeSum(int[] nums) {
        if(nums.length<3 || nums==null) return ret;
        Arrays.sort(nums);
        int len = nums.length;
        for(int i=0;i<len-2;i++) {
            if(i>0 && nums[i]==nums[i]) continue;
            find(nums, i+1, len-1, sum[i]);
        }
        return ret;
    }
    public void find(int[] nums, int start, int end, int target) {
        int l=start, r = end;
        while(l < r) {
            if(nums[l]+nums[r]+target==0) {
                List<Integer> temp = new ArrayList<>();
                temp.add(nums[r]);
                temp.add(nums[l]);
                temp.add(target);
                ret.add(temp);
                while(l<r && [nums[l]==nums[l+1])  l++;
                while(l<r && nums[r]==nums[r-1]) r--;
                l++;
                r--;
            }else if(nums[l]+nums[r]+target < 0) l++;
            else r--;
        }
    }
 }
```
``` java
public class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> ret = new ArrayList<>();
        if(nums.length<3 || nums==null) return ret;
        Arrays.sort(nums); 
        int len = nums.length;
        for(int i=0;i<len-2;i++){
            if(i==0|| (i>0 && nums[i]!=nums[i-1])){
                int l=i+1, r=len-1, temp=0-nums[i];
                while(l<r){
                    if(nums[l]+nums[r]==temp){
                        ret.add(Arrays.asList(nums[l], nums[r], nums[i]));
                        while(l<r && nums[l]==nums[l+1]) l++;
                        while(l <r && nums[r]==nums[r-1]) r--;
                        l++;
                        r--;
                     }else if(nums[l]+nums[r]<temp){
                         while(l<r && nums[l]==nums[l+1])l++;
                         l++;
                     }else{
                         while(l<r && nums[r]==nums[r-1]) r--;
                         r--;
                     }
                }
            }
        }
        return ret;
    }
}
```