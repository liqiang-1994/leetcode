### Binary Tree Level Order Traversal II

Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

* 给定一个二叉树，返回自底向上的层顺序遍历其节点的值(即，从左到右，从叶到根)

```
   3
   / \
  9  20
    /  \
   15   7
   
 Given tree [3,9,20, null, null, 15,7], return 
[
  [15,7],
  [9,20],
  [3]
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
     public List<List<Integer>> levelOrderBottom(TreeNode root) {
         List<List<Integer>> lists = new LinkedList<>();
         levelOrderHelp(lists, root, 0);
         return lists;
      }
      public List<List<Integer>> levelOrderHelp(List<List<Integer>> lists, TreeNode node, int depth) {
         if(node == null) return null;
         if(depth >= lists.size()) {
             lists.add(0, new ArrayList<>());
         }
         levelOrderHelp(lists, node.left, depth+1);
         levelOrderHelp(lists, node.right, depth+1);
         lists.get(lists.size() - depth - 1).add(node.val);
         return lists;
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
   def levelOrderBottom(self, root):
       """
       :type root: TreeNode
       :rtype: List[List[int]]
       """
       lists = []
       self.levelOrderHelp(root, lists, 1)
       return lists
       
    def levelOrderHelp(self, root, lists, depth):
        if not root:
            return False
        if len(lists) < depth:
             lists.insert(0, [])
        self.levelOrderHelp(root.left, lists, depth+1)
        self.levelOrderHelp(root.right, lists, depth+1)
        lists[len(lists)-depth].append(root.val)
```