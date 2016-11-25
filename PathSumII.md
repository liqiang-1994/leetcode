### Path Sum II

Given a binary tree and a sum, find all root-to-leaf paths where each path's sum equals the given sum.

* 给定二叉树和一个数和，找到每个路径的和等于给定和的所有根到叶路径
```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
        
Given sum =22,return 
[
   [5,4,11,2],
   [5,8,4,5]
]
```
``` java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public List<List<Integer>> pathSum(TreeNode root, int sum) {
        List<List<Integer>> ret = new ArrayList<>();
        List<Integer> cur = new ArrayList<>();
        getPath(root, sum, ret, cur);
        return ret;
    }
    public  void getPath(TreeNode root, int sum, List<List<Integer>> ret, List<Integer> cur) {
        if(root ==null) return;
        cur.add(new Integer(root.val));
        if(root.left==null && root.right ==null && root.val == sum) {
            ret.add(new ArrayList<>(cur));
            cur.remove(cur.size()-1);
            return;
         }else{
             getPath(root.left, sum-root.val, ret, cur);
             getPath(root.right, sum-root.val, ret, cur);
          }
          cur.remove(cur.size()-1);
     }
}
```
``` python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution(object):
    def pathSum(self,root, s):
        ret = []
        if nor root:
            return ret
        cur = [(root, [root.val])]
        while cur:
            temp, cal = cur.pop()
            if not temp.left and not temp.right and sum(cal)==s:
                ret.append(cal)
            if temp.left:
                cur.append((temp.left, cal+[temp.left.val]))
            if temp.right:
                cur.append((temp.right, cal+[temp.right.val]))
        return ret
```
``` python
class Solution(object):
    def pathSum(self, root, sum):
        if not root:
            return []
        if not root.left and root.right and root.val==sum:
             return [[root.val]]
        ret = self.pathSum(root.left, sum-root.val)+self.pathSum(root.right, sum-root.val)
        return [[root.val]+i for i in ret]
```
* [这是一位大牛给出的几种python解决的参考](https://discuss.leetcode.com/topic/18444/python-solutions-recursively-bfs-queue-dfs-stack)












