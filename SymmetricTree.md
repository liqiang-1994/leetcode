### Symmetric Tree

Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

* 给定二叉树，判断是否是自身的镜像(即，围绕其中心对称)

```
    1
   / \
  2   2
 / \ / \
3  4 4  3

* 上面的是Symmetric Tree,下面的则不是

   1
   / \
  2   2
   \   \
   3    3
```
``` python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution(object):
    def isSymmetric(self,  root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        if root:
            nums = [(root.left, root.right)]
            while nums:
                left, right = nums.pop()
                if left and right and left.val == right.val:
                    nums.append((left.left, right.right))
                    nums.append((left.right, right.left))
                elif left != right:
                    return False
        return True
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
     public boolean isSymmetric(TreeNode root) {
           return root == null || isSymmetricHelp(root.left, root.right);
       }
     public boolean isSymmetricHelp(TreeNode left, TreeNode right) {
           if(left == null || right == null) return left == right;
           if(left,val == right.val) {
               return isSymmetricHelp(left.left, right.right) && isSymmetricHelp(left.right, right.left);
               }
           else {
               return false;
           }
      } 
 }
```
