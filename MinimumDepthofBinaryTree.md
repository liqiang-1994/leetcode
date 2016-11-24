### Minimum Depth of Binary Tree
Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

* 给定二叉树，找到它的最小深度，最小深度是从根节点到最近叶子节点的最短路径的节点数

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
     public int minDepth(TreeNode root) {
         if(root == null) return 0;
         int left =minDepth(root.left);
         int right = minDepth(root.right);
         return (left ==0 || right ==0) ? left + right +1 : Math.min(left, right) +1;
```

``` python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution(object):
    def minDepth(self, root):
        """
        :type root: TreeNode
        :rtype : int 
        """
        depth, lists = 0, [root]
        while lists and lists[0]:
            depth+=1
            for n in lists:
                if not n.left and not n.right:
                     return depth
            lists = [kids for n in lists for kids in (n.left, n.right) if kids]
        return depth
```
```
class Solution(object):
    def minDepth(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        depth = 0
        if not root:
            return depth
        level = [root]
        while level:
            depth+=1
            temp = []
            for n in level:
                if n.left or n.right:
                    if n.left != None:
                        temp.append(n.left)
                    if n.right != None:
                        temp.append(n.right)
                else:
                    return depth
            level = temp
```