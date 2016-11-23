### Balanced Binary Tree

Given a binary tree, determine if it is height-balanced.

For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of every node never differ by more than 1.

* 给定一个二叉树，判断是否是高度平衡的，高度平衡的二叉树被定义为其中每个节点的两个子树的深度从不相差大于1

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
     public boolean is Balanced(TreeNode root) {
        if(root == null) return true;
        int left = depth(root.left);
        int right = depth(root.right);
        return Math.abs(left - right) <=1 &&  isBalanced(root.left) && isBalanced(root.right);
     }
      public int depth(TreeNode node) {
         if(node == null) return 0;
         return Math.max(depth(node.left), depth(node.right)) +1;
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
    def isBalanced(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        if not root:
            return True
        def depth(node):
            if not node:
                return 0
            return max(depth(node.left), depth(node.right))+1
        return abs(depth(root.left)-depth(root.right)) <=1 and self.isBalanced(root.left) and self.isBalanced(root.right)
```
``` python
class Solution(object):
    def isBalanced(self, root):
        if not root:
            return True
        def depth(node):
            if not node:
                return 0
            left = depth(node.left)
            right = depth(node.right)
            if abs(left - right) > 1:
                raise Exception
            return max(left, right) +1
        try:
            return abs(depth(root.left)-depth(root.right)) <=1
        except:
            return False
            
```