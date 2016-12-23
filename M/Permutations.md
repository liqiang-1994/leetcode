### Permutations

Given a collection of distinct numbers, return all possible permutations.

* 给定不同数字集合，返回所有可能的排列

```
[1,2,3] have the following permutations:

[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]
```
例如，如果输入num []是{1,2,3}：首先，添加1到初始List <List <Integer >>（让我们称之为“answer”）。

因此，我们必须将答案中的List <Integer>复制（它只是{1}），在{1}的位置0添加2，然后再次复制原始{1} ，并在位置1中添加2.现在我们有{{2,1}，{1,2}}的答案。 在当前答案中有2个列表。

然后我们必须添加3.第一个副本{2,1}和{1,2}，在位置0添加3; 然后复制{2,1}和{1,2}，并将3添加到位置1，然后对位置3做同样的事情。最后，我们有2 * 3 = 6列表在答案，这是我们想要的。

``` java
public class Solution {
    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ret = new ArrayList<>();
        ret.add(new ArrayList<Integer>());
        for(int i=0;i<nums.length;i++) {
            List<List<Integer>> temp = new ArrayList<>();
            for(List<Integer> s : ret) {
                for(int j=0;j<s.size()+1;j++) {
                    List<Integer> new_ret = new ArrayList<>(s);
                    new_ret.add(j, nums[i]);
                    temp.add(new_ret);
                }
            }
            ret = new ArrayList<List<Integer>>(temp);
        }
        return ret;
    }
}
```

``` python
class Solution(object):
    def permute(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        rets = [[ ]]
        for n in nums:
            temp = []
            for ret in rets:
                for i in range(len(ret)+1):
                    temp.add(ret[:i] + [n] +[i:])
            rets=temp
        return rets
```