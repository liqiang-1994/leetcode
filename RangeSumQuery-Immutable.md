### Range Sum Query - Immutable

Given an integer array nums, find the sum of the elements between indices i and j (i ≤ j), inclusive.

* 给定整数数组nums，找到索引i和j之间的元素的和，假定数组不变
```
Given nums = [-2, 0, 3, -5, 2, -1]

sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
```

``` java
public class NumArray {
    int[] nums;
    public NumArray(int[] nums) {
        this.nums = nums;
        for(int i=1;i<nums.length;i++){
            nums[i]=nums[i]+nums[i-1];
        }
    }

    public int sumRange(int i, int j) {
        if(i==0) return nums[j];
        return nums[j]-nums[i-1];
    }
}


// Your NumArray object will be instantiated and called as such:
// NumArray numArray = new NumArray(nums);
// numArray.sumRange(0, 1);
// numArray.sumRange(1, 2);
```
``` python
class NumArray(object):
    def __init__(self, nums):
        """
        initialize your data structure here.
        :type nums: List[int]
        """
        self.num = num
        for i in range(1, len(self.num)):
            self.num[i] +=self.num[i-1]
        def sumRange(self, i, j):
        """
        sum of elements nums[i..j], inclusive.
        :type i: int
        :type j: int
        :rtype: int
        """
        return self.num[j] -self.num[i-1] if i >0 else self.num[j]
```




















