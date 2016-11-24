### Path Sum
Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

* 给定二叉树和一个和，确定树是否具有根到叶路径，使得沿路径累积和所有值等于给定和
```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
        
 5->4->11->2 and sum =22, return true
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
    public booelan hasPathSum(TreeNode root, int sum) {
        if(root==null) return false;
        if(root.left==null &&root.right==null && root.val==sum) return true;
        boolean temp1=false, temp2= false;
        if(!(root.left==null)) {
            root.left.val +=root.val;
            temp1 = hasPathSum(root.left, sum);
         }
        if(!(root.right==null)) {
            root.right.val +=root.val;
            temp2 = hasPathSum(root.right, sum);
        }
        return temp1 || temp2;
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
    def hasPathSum(self, root, sum):
        if root == None:
            return False
        if root.left == None and root.right ==None:
            return root.val == sum
        return self.hasPathSum(root.left, sum-root.val) or self.hasPathSum(root.right, sum-root.val)
```