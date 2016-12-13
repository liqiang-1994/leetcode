### Sum of Left Leaves

Find the sum of all left leaves in a given binary tree.

*计算二叉树左叶子的所有和

```
  3
   / \
  9  20
    /  \
   15   7

There are two left leaves in the binary tree, with values 9 and 15 respectively. Return 24.

```
* 使用迭代
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
     public int sumOfLeftLeaves(TreeNode root) {
         if(root==null) return 0;
         int sum= 0;
         if(root.left !=null) {
             if(root.left.left==null && root.left.right==null) sum+=root.left.val;
             else sum+=sumOfLeftLeaves(root.left);
         }
         sum+=sumOfLeftLeaves(root.right);
         return sum;
     }
}
```

* 用栈实现递归
``` python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution(object):
    def sumOfLeftLeaves(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if root == None:
            return 0
        ret = 0
        stack= []
        stack.append(root)
        while stack:
            root = stack.pop()
            if root.left != None:
                if root.left.left ==None and root.left.right==None:
                    ret +=root.left.val
                else:
                    stack.append(root.left)
            if root.right != None:
                if root.right.left !=None or root.right.right !=None:
                    stack.append(root.right)
        return ret
```