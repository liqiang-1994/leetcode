###  Binary Tree Level Order Traversal

Given a binary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

* 给定一个二叉树，返回其节点值的水平顺序遍历
```
    3
   / \
  9  20
    /  \
   15   7
* return 
[
  [3],
  [9,20],
  [15,7]
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
     public List<List<Integer>> levelOrder(TreeNode root) {
         List<List<Integer>> lists = new ArrayList<>();
         levelOrderHelp(root, lists, 0);
         return lists;
      }
      public List<List<Integer>> levelOrderHelp(TreeNode node, List<List<Integer>> lists, int depth) {
          if(node ==null) return null;
          if(depth == lists.size()) {
              lists.add(new ArrayList<>());
          }
         lists.get(depth).add(node.val);
         levelOrderHelp(node.left, lists, depth+1);
         levelOrderHelp(node.right, lists, depth+1);
         return lists;
      }
 }
```

    
    

