### Same Tree

Given two binary trees, write a function to check if they are equal or not.

Two binary trees are considered equal if they are structurally identical and the nodes have the same value.

* 判断两棵树是否相同，结构相同且节点具有相同的值

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
     public boolean isSameTree(TreeNode p, TreeNode q) {
         if(p==null && q==null) return true;
         if(p==null || q==null) return false;
         if(p.val==q.val) return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
         return false;
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
    def isSameTree(self, p, q):
        """
        :type p: TreeNode
        :type q: TreeNode
        :rtype: bool
        """
        stack =[(p, q)]
        while stack:
            m, n = stack.pop()
            if m==None and n==None:
                continue
            elif m==None or n==None:
                return False
            elif m.val==n.val:
                stack.append((m.left, n.left))
                stack.append((m.right, n.right))
            else:
                return False
        return True
```
