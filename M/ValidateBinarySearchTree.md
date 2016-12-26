### Validate Binary Search Tree

Given a binary tree, determine if it is a valid binary search tree (BST).

Assume a BST is defined as follows:

The left subtree of a node contains only nodes with keys less than the node's key. //节点的左子树仅包含具有小于节点的键的键的节点
The right subtree of a node contains only nodes with keys greater than the node's key.//节点的右子树仅包含密钥大于节点密钥的节点
Both the left and right subtrees must also be binary search trees.//左和右子树都必须是二叉搜索树

* 验证二进制搜索树,确定是否是有效的二叉搜索树

```
    2
   / \
  1   3
  Binary tree [2,1,3], return true.
    1
   / \
  2   3
  Binary tree [1,2,3], return false.
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
    public boolean isValidBST(TreeNode root) {
        return help(root, Long.MIN_VALUE, Long.MAX_VALUE);
    }
    public boolean help(TreeNode root, long min, long max) {
        if(root==null) return true;
        if(root.val>=max || root.val<=min) return false;
        return help(root.left, min, root.val) && help(root.right, root.val, max);
     }
 }
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
    public boolean isValidBST(TreeNode root) {
        return help(root, null, null);
    }
    public boolean help(TreeNode root,Integer min, Integer max){
        if(root==null) return true;
        return (min==null||root.val>min) &&(max==null||root.val<max) && help(root.left, min, root.val) && help(root.right, root.val, max);
    }
}
```

``` java
public class Solution {
    public boolean isValidBST(TreeNode root) {
        return helper(root, null, null);
    }
    
    boolean helper(TreeNode root, Integer min, Integer max) {
        if (root == null)
            return true;
        
        if ((min != null && root.val <= min) || (max != null && root.val >= max))
            return false;
        
        return helper(root.left, min, root.val) && helper(root.right, root.val, max);
    }
}
```
``` java
public class Solution {
    public boolean isValidBST(TreeNode root) {
        Stack<TreeNode> stack = new Stack<>();
        TreeNode cur=root;
        TreeNode pre=null;
        while(!stack.isEmpty() || cur !=null){
            if(cur!=null){
                stack.push(cur);
                cur=cur.left;
            }else{
                TreeNode p=stack.pop();
                if(pre!=null && p.val<=pre.val) return false;
                pre=p;
                cur=p.right;
            }
        }
        return true;
    }
}
```