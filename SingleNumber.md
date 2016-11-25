### Single Number

Given an array of integers, every element appears twice except for one. Find that single one.

* 给定一个整数数组，每个元素出现两次，除了一个，找到哪一个

思路：可以利用Hashtable统计每个数子出现的次数，从而求出，不过这道题有一个神奇的解法，异或全部的数值，如果两个相同的数子异或为0，剩下的那个就是要求的数
``` java
public class Solution {
    public int singleNumber(int[] nums) {
        int result = 0;
        for (int n: nums) {
             result ^= n;
          }
          return result;
     }
}
```